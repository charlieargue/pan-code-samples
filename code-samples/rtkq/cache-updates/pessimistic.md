# Pessimistic Example:

```js 
// file: src/hooks/rtk-query/api-and-hooks.js (FRAGMENT)

extendExpirationDate: build.mutation({
    async queryFn({ requestId }, { dispatch, getState }) {
        try {
            const result = await extendExpirationDate(getState, requestId);
            Message.info('Request was successful.', MESSAGE_DISPLAY_DURATION);
            return result;
        } catch (error) {
            return handleReduxError(error, dispatch, setGlobal);
        } finally {
          dispatch(setGlobal({ isFetchingRequests: false }));
        }
    },
    async onQueryStarted({ ...patch }, { dispatch, queryFulfilled }) {
        dispatch(setGlobal({ isFetchingRequests: true }));
        const { data: updatedRequest } = await queryFulfilled;
        dispatch(
            api.util.updateQueryData('getActiveRequests', undefined, draftRequests => {
                const foundDraft = draftRequests.find(
                    request => request.requestId === patch.requestId
                );
                delete foundDraft.isExpiring;
                foundDraft.expirationDate = updatedRequest.expirationDate;
            })
        );
    },
}),
```