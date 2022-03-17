## Transfer Asset - Drawer



### File Organization

<img src="../../_markdown_assets/images/image-20220317004141360.png" alt="image-20220317004141360" style="zoom:67%;" />

### UI Screen Shots



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







DefinitionList.jsx

```jsx  
import { colors, remCalc } from '@Lorem/ipsum';
import styled from 'styled-components';

export const DefinitionList = styled.dl`
    display: grid;
    grid-template-columns: max-content auto;
    width: 100%;
    margin-bottom: remCalc(2);
`;
export const SubTitle = styled.dt`
    grid-column-start: 1;
    font-size: remCalc(10);
    font-weight: 400;
    text-align: right;
    color: ${colors.orange[5]};
    line-height: remCalc(16);
`;
export const Description = styled.dd`
    grid-column-start: 2;
    font-size: remCalc(12);
    font-weight: 400;
    text-align: left;
    color: ${colors.grey[50]};
    padding-left: remCalc(9);
    line-height: remCalc(16);
`;
```

