# Token Automation



### Terminal Screen Shots

![Pasted_Image_3_17_22__4_04_PM](../../_markdown_assets/images/Pasted_Image_3_17_22__4_04_PM.png)



### Code Samples

###### Token.js

```js 
'use strict';
const fs = require('fs');
const path = require('path');
const puppeteer = require('puppeteer');
const targetDirectory = fs.realpathSync(process.cwd());
const minimist = require('minimist');
const readlineSync = require('readline-sync');
const chalk = require('chalk');
const argv = minimist(process.argv.slice(2));
const argEnv = argv._[1];
const resolveSourcePath = relativePath => path.resolve(__dirname, relativePath);
const editEnvFileLines = require('./utils/editEnvFileLines');
const editPackageJsonFileLines = require('./utils/editPackageJsonFileLines');
const LOGIN_URLS = {
    'dev': 'https://lorem.ipsum',
    'stage': 'https://lor em.ipsum',
    'production': 'https://lorem.ipsum'
}
const LOGIN_URL = LOGIN_URLS[argEnv];
const { URLS, SEARCH_STRING_PROXY } = require('./utils/constants');
const KEY_SUPPLEMENT = require(resolveSourcePath('../package.json')).keySupplement;

process.on('unhandledRejection', (err) => {
    throw err;
});

if (!KEY_SUPPLEMENT) {
    console.log(chalk.yellow('ğ KEY_SUPPLEMENT is required, â please add this to your package.json: `"keySupplement": "...key-goes-here..."`'));
    process.exit(1);
}

if (!process.env.REACT_APP_PAN_ENCRYPTED_PWD) {
    console.log(chalk.yellow('ğ REACT_APP_PAN_ENCRYPTED_PWD is required: \n\tâ please run: `lorem-ipsum encrypt-pwd` \n\tâ or maybe you need to RESTART your terminal?'));
    process.exit(1);
}

if (!argEnv) {
    console.log(chalk.yellow('ğ environment argument is required, â eg. `lorem-ipsum token dev|stage|prod`'));
    process.exit(1);
}

if (!['sit', 'stg', 'qa'].includes(argEnv)) {
    console.log(chalk.yellow('ğ incorrect environment argument, â needs to be one of: `dev|stage|prod`'));
    process.exit(1);
}

process.env.NODE_ENV = 'development';
require('../config/env');


// ##################################################################################
// # TOKEN automation (w/ puppeteer)
// ##################################################################################
(async () => {
    try {

        // 1. Get Security PIN
        // 2. Automate Login
        // 3. Get Portal Context
        // 4. Update .env File
        // 5. Update package.json

        const pin = readlineSync.question(`\nEnter your ğ¡ secure 4 character PIN: `, { hideEchoBack: true });
        console.log(chalk.yellow(`ğ STEP 1/3: Logging in to CSP environment:['${argEnv}']...`));
        const { authToken, userAccountId } = await automateLoginAndGetLoremIpsum(pin);

        console.log(chalk.yellow(`ğ STEP 2/3: Updating your ğ¸ .env ğ¸ variables...`));
        await updateEnvFile(authToken, userAccountId);

        console.log(chalk.yellow(`ğ STEP 3/3: Updating your ğ¸ package.json ğ¸ proxy...`));
        await updatePackageJsonProxy(URLS[argEnv]);

        console.log(chalk.yellow('â Done! You can now run `npm start` or `lorem-ipsum msw`'));


    } catch (err) {
        if (err && err.message) {
            console.log(err.message);
        }
        process.exit(1);
    }

})();


// ------------------------
async function automateLoginAndGetLoremIpsum(pin) {
    try {
        const browser = await puppeteer.launch({
            headless: true,
            ignoreHTTPSErrors: true,
            acceptInsecureCerts: true,
        });
        const page = await browser.newPage();
        await page.setDefaultNavigationTimeout(0);
        await page.goto(LOGIN_URL);

        // wait for username input
        const usernameSelector = '.form-control';
        await page.waitForSelector(usernameSelector);
        await page.type(usernameSelector, process.env.REACT_APP_USER_EMAIL_ADDRESS);
        await page.click('#lorem-ipsum');

        // password reading
        const encryptor = ... // SANITIZED
        const decryptedPassword = ... // SANITIZED
        const pwdSelector =  ... // SANITIZED
        await page.waitForSelector(pwdSelector);
        await page.type(pwdSelector, decryptedPassword);
        page.keyboard.press('Enter');

        // await and grab necessary properties
        const watchDog = page.waitForFunction('window.LoremIpsum !== undefined', { timeout: 0 });
        await watchDog;
        const result = await page.evaluate(() => window.LoremIpsum);
        await browser.close();
        return result;
    } catch (err) {
        throw new Error('ğ AUTOMATION ERROR: perhaps you entered your ğ¡ PIN incorrectly? ')
    }
}

// ------------------------
async function updateEnvFile(authToken, userAccountId) {
    const ENV_FILENAME = '.env';
    const envFile = path.resolve(targetDirectory, ENV_FILENAME);
    if (fs.existsSync(envFile)) {
        await editEnvFileLines(envFile, authToken, userAccountId, argEnv);
    } else {
        console.log(chalk.red(`ğ Uh-oh, could not find /${ENV_FILENAME}, so could not update... ABORTING...`));
        process.exit(1);
    }
}
// ------------------------
async function updatePackageJsonProxy(url) {
    const PKG_JSON_FILENAME = 'package.json';
    const pkgJsonFile = path.resolve(targetDirectory, PKG_JSON_FILENAME);
    if (fs.existsSync(pkgJsonFile)) {
        const replaceString = `    "proxy": "${url}",`;
        await editPackageJsonFileLines(pkgJsonFile, SEARCH_STRING_PROXY, replaceString);
    } else {
        console.log(chalk.red(`ğ Uh-oh, could not find /${PKG_JSON_FILENAME}, so could not update... ABORTING...`));
        process.exit(1);
    }
}
```



