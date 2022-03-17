# General (from Component) Example:

```js 
// file: src/components/popovers/incoming/IncomingPopover.jsx (FRAGMENT)

const onAcceptClick = async () => {
    await triggerAccept({ userAccountId, supportAccountId, deviceTransferId });
    setAlertVisibility(ALERT_VISIBILITY_STATES.ACCEPTED_ALERT);
    setTimeout(() => {
        dispatch(
            api.util.updateQueryData(
                'getPendingAssets',
                { userAccountId, supportAccountId },
                (drafts) => {
                    drafts.splice(
                        drafts.findIndex((draft) => draft.device_transfer_id === deviceTransferId,
                        ),
                        1,
                    );
                }));
    }, PO_ALERT_TIMEOUT);
};
```

