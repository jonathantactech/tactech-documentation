# Instructions

Las importaciones se deben realizar en el siguiente orden:

1. Importar librerías.
2. Importar componentes con alias (~folder5/folder6/Component). Se deben separar con salto de linea.
3. Previos directory (‘../../Component’;)
4. Current directory (‘./Component’)

## Example

```jsx
import React, { PureComponent } from 'react';
import { connect } from 'react-redux';
import PropTypes from 'prop-types';
import { change, getFormValues } from 'redux-form';

import { boxPropTypes } from '~common/propTypes/productPropTypes';

import { distributionOrderPropTypes } from '~logistic/propTypes/DistributionOrderPropTypes';

import { logisticsActions } from '~logistic/redux/actions';

import { modalActions } from '~common/redux/actions';

import { PURCHASE_ORDER_STATUS } from '~logistic/constants/sodimacLogistics';

import { isFromChile } from '~common/constants/countries';

import { errorMessages } from '../../errors';
import { getDistributionOrderWithdrawDate } from '../../utils';
import { MFN_ORDER_STEPS_FORM, EDITION_CONFIRMATION_MODAL } from '../../constants';

import { MONO_SKU } from './constants';
import PackagingStep from './layout';
import {
  getUnassignedProducts,
  removeQuantitiesToUnassignedProducts,
  addProductsToBox,
  unassignedProductsAfterRemovingProductFromBox,
  unassignedProductsAfterRemovingBox,
  hasSingleProduct,
  formatProductsQuantity,
  formatPackagingData,
  formatBoxes,
  setDefaultDimensionsForm
} from './utils';
```

### .babelrc (svl-frontend-react)
```json
{
  "plugins": [
    [
      "module-resolver",
      {
        "root": ["./src"],
        "alias": {
          "~scss": "./src/scss",
          "~common": "./src/app/common",
          "~product": "./src/app/product",
          "~user": "./src/app/user",
          "~core": "./src/app/core",
          "~logistic":  "./src/app/logistic",
          "~finances":  "./src/app/finances",
          "~reports":  "./src/app/reports" 
        }
      }
    ],
    [
      "transform-runtime",
      {
        "polyfill": false,
        "regenerator": true
      }
    ]
  ],
  "presets": ["react", "es2015", "stage-0"]
}
```