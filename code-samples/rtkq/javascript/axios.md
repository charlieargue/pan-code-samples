#### "Fetcher" Service based `axios` (for RTK-Q)

```js 
// file: src/utils/axiosBaseQuery.js

import axios from 'axios';
import { handleErrorAPI } from './error-handling/handleErrorAPI';
import { getHeaders } from './getHeaders';

// ##################################################################################
// axios BASE QUERY (for rtkq)
// ##################################################################################
export const axiosBaseQuery =
    () =>
    async (requestOptions, { getState }) => {
        try {
            const { auth } = getState();
            const { baseUrl } = auth;
            const defaultHeaders = getHeaders(auth);
            const options = {
                ...requestOptions,
                headers: {
                    ...defaultHeaders,
                    ...requestOptions.headers,
                },
                url: baseUrl + requestOptions.url,
            };
            const result = await axios(options);
            handleErrorAPI(result);
            return { data: result?.data.data || result.data };
        } catch (axiosError) {
            return {
                error: {
                    status: axiosError.response?.status,
                    data: axiosError.response?.data,
                },
            };
        }
    };

export default axiosBaseQuery;
```

