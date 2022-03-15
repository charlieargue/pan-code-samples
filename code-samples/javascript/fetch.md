# "Fetcher" Service based on `fetch`

```js 
import { getDefaultPayload, getHeaders, handleErrorAPI } from '@lorem/ipsum';

const DEFAULT_OPTIONS = {
    method: 'POST',
    getState: () => {},
    body: () => {},
    params: () => {},
};

// ##################################################################################
// # Abstraction for fetch-based requests
// ##################################################################################
export const fetcherService = async (options = DEFAULT_OPTIONS) => {
    const mergedOptions = {
        ...DEFAULT_OPTIONS,
        ...options,
    };
    const { auth } = mergedOptions.getState((freshState) => freshState);
    let url = mergedOptions.url ? `${auth.baseUrl}${mergedOptions.url}` : auth.baseUrl;
    const fetchOptions = {
        method: mergedOptions.method,
        headers: getHeaders(auth),
    };
    if (mergedOptions.params) {
        url += `?${new URLSearchParams(mergedOptions.params(auth))}`;
    }
    if (['POST', 'PUT', 'PATCH'].includes(mergedOptions.method)) {
        const body = JSON.stringify({
            ...getDefaultPayload(auth),
            ...mergedOptions.body(auth),
        });
        fetchOptions.body = body;
    }
    const result = await fetch(url, fetchOptions);
    const unpacked = await result.json();
    handleErrorAPI(unpacked);
    return unpacked;
};
export default fetcherService;
```

