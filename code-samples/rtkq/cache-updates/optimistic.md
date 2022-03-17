#### Optimistic Example:

```js 
// file: src/rtkq/builders/getPendingAssetsBuilder.js (FRAGMENT)

onQueryStarted(
  { userAccountId, supportAccountId, deviceTransferId }, 
  { dispatch, queryFulfilled }) {
  const fresh = dispatch(
      api.util.updateQueryData(
          'getPendingAssets',
          { userAccountId, supportAccountId },
          drafts => {
              const foundDraft = drafts.find(draft => 
                       draft.device_transfer_id === deviceTransferId);
              Object.assign(foundDraft, {
                  device_transfer_state: TRANSFER_STATUS.ACCEPTED,
              });
          }
      )
  );
  queryFulfilled.catch(fresh.undo);
},
```

