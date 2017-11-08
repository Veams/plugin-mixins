# VeamsMixins plugin

The VeamsMixins plugin is something where you can save global mixins. Mixins are object with functions in it which can be used to extend methods in other classes/modules.

```js
import Veams from 'veams';
import VeamsMixins from 'veams/lib/plugins/mixins';

// Intialize core of Veams
Veams.onInitialize(() => {
  // Add plugins to the Veams system
  Veams.use(VeamsMixins);
});
```

_API:_

When enabled the API provides a way to add a mixin to the container `Veams.mixins`.

###### Veams.addMixin('name', mixinFunction)

* @param {`String`} name - Mixin name which will be used in the registration process.
* @param {`Function`} mixinFunction - The mixin function should return an object with methods.

The method allows the registration of provided or custom mixins.

```js
import Veams from 'veams';
import VeamsMixins from 'veams/lib/plugins/mixins';

import imageLoader from './utils/mixins/image-loader';

// Intialize core of Veams
Veams.onInitialize(() => {
  // Add plugins to the Veams system
  Veams.use(VeamsMixins);
  Veams.addMixin('imageLoader', imageLoader);
});
```

Later you can use this specific mixin in other modules:

```js
myClass.mixin(Veams.mixins.imageLoader);
```

Here you see that you need to extend your custom class with the helper function `mixin`, which is available in `Veams.helpers`.
