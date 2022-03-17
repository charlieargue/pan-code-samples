## Transfer Asset - Drawer



### File Organization

<img src="../../_markdown_assets/images/image-20220317004141360.png" alt="image-20220317004141360" style="zoom:67%;" />

### UI Screen Shots

- [ ] 🔥 TODO (grab from looms)





### Loom Videos

- [ ] 🔥 TODO



### Component Map

![image-Transfer-Asset-Drawer-CMNPT-MAP](../../_markdown_assets/images/image-Transfer-Asset-Drawer-CMNPT-MAP.png)



### Code Samples:

TransferDrawer.jsx

```jsx  
import { bool, func } from 'prop-types';
import React from 'react';
import { useSelector } from 'react-redux';

import { assetPropType } from '../../assetPropType';
import { DrawerContents } from './DrawerContents';
import Base from './TransferDrawer.styles';

// ##################################################################################
// # Asset TRANSFER Drawer
// ##################################################################################
export const TransferDrawer = ({ visible, onClose, record }) => {
    const drawerContentsProps = {
        visible,
        record,
        onClose
    };

    const { maskLocked } = useSelector((state) => state.drawer);

    // NOTE: destroyOnClose: means that any state on Base will NOT get destroyed, only Base's children's state will get destroyed
    return (
        <Base
            width={541}
            title={<h1>Transfer Asset</h1>}
            visible={visible}
            onClose={onClose}
            maskClosable={!maskLocked}
            destroyOnClose>
            <DrawerContents {...drawerContentsProps} />
        </Base>
    );
};

TransferDrawer.propTypes = {
    visible: bool,
    onClose: func,
    record: assetPropType,
};

export default TransferDrawer;
```



TransferDrawer.styles.js

```js 
import { SideDrawer } from '@Lorem/Ipsum';
import styled from 'styled-components';

export default styled(SideDrawer)`
    .ant-drawer-body {
        display: flex;
        flex-direction: column;
        align-items: flex-start;

        & > .ant-card {
            margin-bottom: 28px;
        }

        & > .ant-table-wrapper {
            margin-bottom: 12px;
        }

        & > a,
        & > button {
            align-self: flex-end;
        }
    }
`;
```





Heading.jsx

```jsx  
// file: src/components/assets/drawers/TransferDrawer/heading/Heading.jsx
import { colors, units } from '@Lorem/Ipsum';
import React from 'react';
import styled from 'styled-components';

import { assetPropType } from '../../../assetPropType';
import { Title } from '../typography';

const DefinitionList = styled.dl`
    display: grid;
    grid-template-columns: max-content auto;
    width: 100%;
    margin-bottom: ${remCalc(2)};
`;
const SubTitle = styled.dt`
    grid-column-start: 1;
    font-size: ${remCalc(12)};
    text-align: right;
    color: ${colors.grey[60]};
    border-bottom: ${remCalc(1)} solid ${colors.grey[30]};
    height: ${remCalc(36)};
    line-height: ${remCalc(32)};
    &.first {
        line-height: ${remCalc(16)};
        height: ${remCalc(29)};
    }
`;
const Description = styled.dd`
    grid-column-start: 2;
    font-size: ${remCalc(12)};
    font-weight: 400;
    text-align: left;
    color: ${colors.grey[90]};
    padding-left: ${remCalc(17)};
    border-bottom: ${remCalc(1)} solid ${colors.grey[30]};
    height: ${remCalc(36)};
    line-height: ${remCalc(32)};
    &.first {
        line-height: ${remCalc(16)};
        height: ${remCalc(29)};
    }
`;
// ##################################################################################
// HEADING
// ##################################################################################
export const Heading = ({ record }) => {
    return (
        <>
            <Title>Asset to be Transferred</Title>
            <DefinitionList>
                <SubTitle className='first'>Asset Type:</SubTitle>
                <Description className='first'>{record.type_name}</Description>
                <SubTitle>Model:</SubTitle>
                <Description>{record.model_name}</Description>
                <SubTitle>Asset Name:</SubTitle>
                <Description>{record.name}</Description>
                <SubTitle>Serial Number:</SubTitle>
                <Description>{record.serial_number}</Description>
            </DefinitionList>
        </>
    );
};

Heading.propTypes = {
    record: assetPropType,
};

export default Heading;
```



DefinitionList.jsx

```jsx  
import { colors, remCalc } from '@Lorem/ipsum';
import styled from 'styled-components';

export const DefinitionList = styled.dl`
    display: grid;
    grid-template-columns: max-content auto;
    width: 100%;
    margin-bottom: ${remCalc(2)};
`;
export const SubTitle = styled.dt`
    grid-column-start: 1;
    font-size: ${remCalc(10)};
    font-weight: 400;
    text-align: right;
    color: ${colors.orange[5]};
    line-height: ${remCalc(16)};
`;
export const Description = styled.dd`
    grid-column-start: 2;
    font-size: ${remCalc(12)};
    font-weight: 400;
    text-align: left;
    color: ${colors.grey[50]};
    padding-left: ${remCalc(9)};
    line-height: ${remCalc(16)};
`;
```











### Cypress UI Integation Testing (E2E) & StoryBook - Code Samples:

TransferDrawer.stories.jsx (**StoryBook**)

```jsx  
import React from 'react';

import { TransferDrawer } from '.';
import { MOCKED_RESPONSE_ASSET_DETAILS } from '../../../../mocks/mock-responses';

export default {
    title: 'Drawers > Transfer Drawer',
    component: TransferDrawer,
};

const Template = (args) => (
    <table>
        <tbody>
            <tr>
                <td>
                    <TransferDrawer
                        {...args}
                        record={MOCKED_RESPONSE_ASSET_DETAILS.data}
                        visible
                        onClose={() => {
                            console.log('🚀 ~ Closed...');
                        }}
                    />
                </td>
            </tr>
        </tbody>
    </table>
);

export const Primary = Template.bind({});
Primary.args = {
    primary: true,
    label: 'TransferDrawer',
};
```



TransferDrawer.spec.js (**Cypress**)

```jsx  
/* eslint-disable no-undef */
import { MOCKED_RESPONSE_ASSET_DETAILS } from '../../../../mocks/mock-responses';

const COMPONENT_SB_PATH = '/iframe.html?path=/story/drawers-transfer-drawer--primary';
const DRAWER_BODY = '.ant-drawer-body';
// ##################################################################################
// CYPRESS + STORYBOOK
// ##################################################################################
describe('TRANSFER Drawer', () => {
    beforeEach(() => {
        cy.visit(COMPONENT_SB_PATH);
    });

    it('title should  be correct', () => {
        cy.get('.ant-drawer-title > h1').contains('Transfer Asset');
    });

    it.only('“Assets to be transferred” heading area is populated correctly', () => {
        cy.get(DRAWER_BODY).contains('Asset to be Transferred');

        // labels + values
        cy.get(DRAWER_BODY).contains('Asset Type:');
        cy.get(DRAWER_BODY).contains(MOCKED_RESPONSE_ASSET_DETAILS.data.type_name);

        cy.get(DRAWER_BODY).contains('Model:');
        cy.get(DRAWER_BODY).contains(MOCKED_RESPONSE_ASSET_DETAILS.data.model_name);

        cy.get(DRAWER_BODY).contains('Asset Name:');
        cy.get(DRAWER_BODY).contains(MOCKED_RESPONSE_ASSET_DETAILS.data.name);

        cy.get(DRAWER_BODY).contains('Serial Number:');
        cy.get(DRAWER_BODY).contains(MOCKED_RESPONSE_ASSET_DETAILS.data.serial_number);
    });

    // ... 

});
```

