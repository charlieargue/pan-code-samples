# Example #1: Get Pending Assets - Builder

```js 
// file: src/rtkq/builders/getPendingAssetsBuilder.js
const url = '/api/Lorem/Ipsum';

export const getPendingAssetsBuilder = (builder) =>
    builder.query({
        query: ({ userAccountId, supportAccountId }) => {
            return {
                url,
                method: 'GET',
                params: { userAccountId, supportAccountId },
            };
        },
        providesTags: result =>
            result
                ? [
                    ...result?.map(
                        ({ device_transfer_id }) =>
                            ({ type: 'Transfer', id: device_transfer_id })),
                    { type: 'Transfer', id: 'LIST' },

                ]
                : [{ type: 'Transfer', id: 'LIST' }],
    });

export default getPendingAssetsBuilder;
```