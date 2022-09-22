Grid products react client library.

Example:

```js
import React from 'react';
import { useGridProductsClient } from '@ombori/grid-products-client-react';

const useProductVariant = (id) => {
  const [variantDetails, setVariantDetails] = React.useState(null);

  const gp = useGridProductsClient({
    environment: 'PROD'
  });

  React.useEffect(() => {
    const getVariantDetails = async() => {
      const details = await gp.getVariantDetails(id);
      setVariantDetails(details);
    }

    if (id) {
      getVariantDetails();
    }
  }, [id]);
}
```