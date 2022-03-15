# 📊 Flowcharts and Diagrams



### My "Testing Pyramid"

From a personal project ([multicart](https://www.multicart.app/))

![testing-pyramid](../_markdown_assets/images/testing-pyramid-20220319093743412.png)



### Tech Debt & Refactoring Journey

A simplified flow-chart highlighting key points in the path I took to successfully remove a huge amount of technical debt and refactor multiple MFEs, while simultaneously delivering much-loved new UI features:



```mermaid
graph TD
      A(Converting remaining CLASS COMPONENTS to Functional) --> |DRY-ing and SRP-ing|B(upgrades and bug fixes to legacy & new DESIGN SYSTEMS)
      B --> |file and folder RE-ORGANIZATION| C(building TESTABLE components)
      C --> D[SEPARATION of App State from Server State]
      C --> |removing unnecessary PROP DRILLING| E[service and DEPENDENCY INJECTION improvements]
		  D --> F(fixing errors and potential MEMORY LEAKS with useSafeDispatch and useIsMounted)
		  E --> F
		  F --> G(latest patterns and best practices)
		  G --> |swr VS react-query VS RTK-Q| H(CACHE strategies and configuration)
		  G --> |pure React Context VS react-tracked VS RTK| I(state management POC, ctx-options)
		  H --> J(rigorous and efficient testing and debugging)
		  I --> J
		  J --> |Jest, Cypress E2E Tests, and Postman| K(using msw to MOCK entire APIs)
		  K --> L(Upgrades propagated to other MFEs and to MFE boilerplate)
		  L --> |kick-starting other micro-frontends| M(Optimizing for performance and eliminating unnecessary renders)
		  M --> |loading spinners, skeletons, and animations| N(adding Error Boundaries)
		  N(CLI, tooling, and React-Scripts upgrades) --> |babel / Jest / webpack / eslint / prettier configs| O(working with an ejected Creact-React-App)
		  O --> P(coding up production fixes for tooling)
		  subgraph i
        C
        D
        E
      end
      subgraph ii
        G
        H
        I
      end
      subgraph iii
        N
        O
        P
      end
```





### Simplified "Where to Put State" Flow Chart

Inspired by [Kent Dodds' decision tree chart](https://kentcdodds.com/blog/state-colocation-will-make-your-react-app-faster#so-how-do-you-decide-where-to-put-state):

```mermaid
graph TD
      A(Where to put state?) --> B(#1 - data fetching and cache management tool)
      B --> |eg. RTK-Q| C{#2 - If not server state, then app state:}
      C --> D(useState)
      C --> E(lift or co-locate)
      C --> F(component composition)
      C --> G(prop drilling)
      C --> H(Context)
      D --> I(#3 - Redux)
      E --> I
      F --> |... and as a last resort ...|I
      G --> I
      H --> I
```



### My "JIRA Process" 

From a FE Perspective:

```mermaid
graph TD
      A(("🎽 Start with an EPIC")) --> B("🏋️‍♀️Medium-to-hard sprint points need a short DESIGN DOC")
      B --> |"🎨 UI/UX Figma, prototypes, hand-offs"| C("📌 `PIN POINTS` mapping each endpoint to UI/UX")
      C --> D("📬 POSTMAN  endpoints, payloads, etc.")
      D ==> |if design doc exists| E{"🖋 Team sign-off on design doc"}
      E --> |Assign to team members| F("🪓  Break into STORIES, write full AC/requirements, weigh points")
      F --> |FE, BE, PROXY, INTEGRATION stories| G("🖨 Clone stories as needed for team")
      G --> |Use JIRA templates I provided| GG("🔪 Break stories into SUB-TASKS, if needed")
      GG --> |"🗣 Shout-outs on any blockers"| H("👷‍♂️👷‍♀️ Development work ...🚧")
      H --> |Finalize any stubbed-out Postman endpoints| GG
```

