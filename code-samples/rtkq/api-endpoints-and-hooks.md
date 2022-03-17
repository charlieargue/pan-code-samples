# Example #1

```js 

import { api } from '../rtkq/api';
import { acceptTransferBuilder, getFiltersBuilder, getPendingAssetsBuilder, getPrivilegesBuilder, rejectTransferBuilder } from '../rtkq/builders';

// ##################################################################################
// 
// QUERY USAGE: `
//      const { isLoading, error, data } = useFooQuery();`
//      const { isLoading, error, data, refetch } = useFooQuery({skip: true});`
//      const [trigger, result, lastPromiseInfo] = useLazyGetPostsQuery(options)
//      const result = await trigger({argOne, argTwo});
//
// MUTATION USAGE: `
//      const [foo, { isLoading }] = useFooMutation();`
// 
// ##################################################################################
const extendedApi = api.injectEndpoints({
    endpoints: (build) => ({
        getPrivileges: getPrivilegesBuilder(build),
        getFilters: getFiltersBuilder(build),
        getPendingAssets: getPendingAssetsBuilder(build),
        acceptTransfer: acceptTransferBuilder(build),
        rejectTransfer: rejectTransferBuilder(build),
    }),
    overrideExisting: false,
})


export const {
    useGetPrivilegesQuery,
    useGetFiltersQuery,
    useLazyGetPendingAssetsQuery,
    useLazyAcceptTransferQuery,
    useLazyRejectTransferQuery,
    useLazyResubmitTransferQuery,
} = extendedApi;
```

