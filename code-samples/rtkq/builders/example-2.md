#### Example #2: Start Transfer - Builder

```js 
// file: src/rtkq/builders/startTransferBuilder.js
const url = '/api/Lorem/Ipsum';

export const startTransferBuilder = (builder) =>
    builder.mutation({
        query: ({ userAccountId, supportAccountId, formValues, record }) => {
            return {
                url,
                method: 'POST',
                params: {
                    userAccountId,
                    supportAccountId,
                },
                body: buildBody(supportAccountId, formValues, record)
            };
        },
        invalidatesTags: (result, error, { record }) => {
            return [{ type: 'Asset', id: record.id }];
        },
    });

function buildBody(supportAccountId, formValues, record) {
    let transferBy;
    let destination;
    if (formValues['transfer-destination'] === 'USER') {
        transferBy = "EmailRecipient";
        destination = {
            destination_email: formValues.email,
        };

    } else if (formValues['transfer-destination'] === 'SUPPORT_ACCOUNT') {
        transferBy = "SupportAccount";
        destination = {
            support_account_id: supportAccountId,
        };

    }
    const payload = {
        device_id: record.id,
        device_name: record.name,
        has_asc_transfer_access: false,
        has_lgs_associated: record.has_lgs_associated,
        notify_user: formValues['notify-user'],
        part_number: null, // legacy, can be null
        serial_number: record.serial_number,
        transfer_by: transferBy,
        ...destination,
    };
    return payload;
}

export default startTransferBuilder;
```