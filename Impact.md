# 🚀 Positive Impact 



### `Impact on:` Testing & Mocking

- Introduced a modern **testing infrastructure** **and tooling** (`msw`, Jest, Cypress), centralized so developers could use them from any MFE (including Jest and Cypress code coverage)

- Setup next-generation **API mocking** (`msw`), that allowed effortless request interception at the network level, and seamless re-use the same mock definitions for testing, development, and debugging

- Demonstrated successful use of **Cypress E2E tests** to confidently and quickly refactor entire MFEs, to hunt/fix/prevent bugs, and as a UI unit and component testing tool (against StoryBook)

- Introduced Postman as a critical tool for sharing collections between BE and FE teams

- While refactoring multiple MFEs and building new features, wrote **clean, bug-free, and highly-testable code** so that services, components, utility functions, and custom hooks could all be exercised rigorously

- Guided team on what to test and how to test (see [Testing Pyramid](https://github.com/charlieargue/multi-cart#-testing), eg. how Jest component tests should check for an even handler being called where-as E2E tests should test that a toast message appeared, etc.)

- **🚀 IMPACT:** 

  - Solved FE team's primary pain point of blockage by BE dysfunction and unstable BE environments
  - Super-charged development velocity and allowed for rapid prototyping
  - Developers stopped putting messy mocking code all over the codebases
  - Staff engineer started using Cypress/Jest/Postman/`msw` and our joint efforts led to complete adoption by the team
  - No testing was being done on my team when I arrived, and now the staff engineer and team are writing tests regularly
  - `msw/data` in particular allowed for mocked data persistence and allowed for effectively mocking entire complex workflows and building out entire features without waiting for the BE
  - Greatly improved team's capability to deliver bug-free features

  

### `Impact on:` UI/UX Design

- Made the designer very happy with pixel-perfect build-outs of his Figma prototypes (thx [PerfectPixel](https://chrome.google.com/webstore/detail/perfectpixel-by-welldonec/dkaagdgjmgdmbnecmcefdhjekcoceebi?hl=en)!)
- Provided frequent useful feedback on better UI design (eg. better design of toasts and alerts for popovers in a DataTable context)
- Solved a major Data View pain-point by combining loading states for Asset Dashboard Tiles, Product Families, Search, Filters, and Data Table UI/UX, removing the need for a lot of code and buggy edge-cases



### `Impact on:` Supervising Staff Engineer 

- [ ] Provided regular guidance to my supervising **staff engineer** on the **latest** React (and general software) best practices, patterns, and trends — he  adopted almost all of my suggestions, including but not limited to:

  - [ ] Advanced use of markdown and **Typora** (a markdown editor)

  - [ ] having a centralized, markdown-based **"Personal Knowledge Base"** in GitHub

  - [ ] switching to **MBP** (and guidance on setup and optimization)

  - [ ] following **React community leaders** such as Kent Dodds, Ben Awad, as patterns such as Tao of React, "Rule of Three" or "AHA Programming"

  - [ ] purchasing the **Epic React** and **JavaScript Testing workshops** by Kent Dodds, upon my personal recommendation

  - [ ] using **Tabox** for Chrome tab group management

  - [ ] using **Github Desktop**

  - [ ] **VSCode extensions**: auto-imports, spell checker, snippets, Quokka, themes, #region folding, bookmarks, Markdown to JIRA, CODDX Kanban Board, Turbo Console Log, Auto Barrel, and others

  - [ ] using **VSCode keyboard short-cuts** such as: auto-order/dedupe imports, auto-formatting, navigate back/forward, etc.

  - [ ] fixed annoying prettier auto-format that was running each time a developer saved a file, to instead run before commits via **`husky`**

  - [ ] **separating state** into two categories: App state from Server state (and not keeping everything in Redux)

  - [ ] successfully implementing various **latest patterns and libraries** for state-management, data fetching, and cache management options, including pure React Context, react-tracked, react-query, and RTK-Q (Redux was already being used)                                          

  - [ ] clearing up misunderstandings that caused the team to shy away from pure **React Context**

  - [ ] provided clear **POC** repo [ctx-options](https://github.com/charlieargue/ctx-options) to demonstrate common state management solutions and patterns for dealing with React Context over-renders

  - [ ] successfully pushing leadership to setup a shared **PostMan** collection for the team

  - [ ] centralizing library exports and **cheatsheets** in a separate dev-tools repo

  - [ ] establishing **caching** patterns and strategies

  - [ ] next generation **API mocking** for testing and development

  - [ ] component-based **rapid prototyping** with StoryBook (and then using those stories for component UI unit tests via Cypress)

    

### `Impact on:` Other Junior & Senior Team Members

- [ ] taking less experienced dev under my wing and helping thru frequent pair programming sessions
- [ ] guidance on entire dev workflows, specifically how to use:
  - [ ] StoryBook for **rapid UI prototyping**
  - [ ] `msw` and `@mswjs/data` for **rapid development** against a mocked API (wiring up data and behavior)
  - [ ] Postman, Jest, and Cypress for building an efficient and robust **testing pyramid**
  - [ ] other tips and best practices (see cheatsheet)



### `Impact on:` Team Productivity & DX

- [ ] repetitive chore automation 💚 (via puppeteer, positively affected dozens of MFEs and environments)
- [ ] linking, starting, and msw command shortcuts (via `zsh` config)
- [ ] VSCode extensions, chrome extensions, see MBP cheatsheet
- [ ] husky & the DISABLE_PRETTIER flag (before that, each time a developer would save their file, the prettier auto-format would run, losing their place on the screen, un-folding all folded code, and causing all sorts of other headaches)
- [ ] using [loom](https://www.loom.com/) videos to quickly and easily communicate status updates on features, and much more



### `Impact on:` Agile and Project Management

<u>Guided project management on:</u>

- proper Acceptance Criteria
- epic kick-offs (w/ design-docs for medium-to-hard stories)
- post-mortems
- 1-on-1s 

- having Retros at end of sprint instead of during sprint
- NOT re-defining Stand-ups (they wanted to change them to be normalized around features instead of team members)
- splitting FE from BE in stand-ups
- de-coupling FE from BE in stories (separate integration stories)
- keeping stand-ups short, using call-outs in JIRA and slack, and leaning out amount of meetings
- how to switch from Visual to Text editing mode
- benefits of markdown, mocking API servers, creating sub-tasks (of stories), linking issues, sharing Postman collections, and more
- markdown tips & tricks:
  - auto-outlining syntax
  - how to attach images inline (and not at bottom) of description
  - how to insert tables and formatted code blocks

- lessening the amount of meetings (amount was affecting the team's development productivity)
- guidance on team prep for Sprint Planning



### `Impact on:` Future Directions

Created momentum, enthusiasm, and consensus on future architectural decisions and upgrades, such as:

- [ ] upgrading to **Next.js** (team now even considering **Remix**!)
- [ ] migrating to a **monorepo**, such as **NX**  (team now even considering **TurboRepo**!)
- [ ] running Cypress E2E tests in **CICD** via **GitHub actions** and **Cypress Dashboard** (provided .yml scripts for running E2E tests in parallel, across multiple machines)
- [ ] guidance on how to create **"Testing Sandboxes"** (by dynamically generating test roles, accounts, users, assets, etc.)
- [ ] guidance on switching from rapid prototyping in Storybook and then Cypress, to just Cypress via **Component Test Runner**
- [ ] guidance on how to setup screenshot **UI Regression Testing** (via Happo, StoryBook, and Cypress)
- [ ] guidance on using [Plop](https://plopjs.com/) to **automatically generate** and scaffold new files with consistency

