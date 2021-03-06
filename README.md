># Ormson
>Artisan ORM for JSON databases

### Installation
1. `npm install ormson`

### Use
To use ORMSON you need to create the models you need within the path `models/` and then require the `index` file that found in the models folder where you want to use it.

It is important to have installed the ormon client and have generated the necessary folder structure to be able to use Ormson.

More info: https://www.npmjs.com/package/ormson-cli

### Template model

```js script
const Ormson = require('ormson');

class Product extends Ormson {
    constructor() {
        super();
        this.define({
            name: {
                type: String,
                required: true,
                validator: name => name.length > 10
            },
            price: {
                type: Number,
                required: true,
                validator: price => price > 0
            }
        }, {
            tablename: 'products',
            location: __filename
        });
    }
}

module.exports = Product;
```

### Require example
```js script
 const { Product } = require('./database/models');
```

### Methods

Method                               | Description                           | Example
------------------------------------ | ------------------------------------- | --------------------------------------
**findAll(*option: callback*)**      | Search for multiple instances.        | `Model.findAll();`</br>`Model.findAll((row) => row.column == 'value');`
**findOne(*callback*)**              | Find an instance by condition.        | `Model.findOne((row) => row.column == 'value');`
**findByPk(*id*)**                   | Find an instance by id.               | `Model.findByPk(12);`
**create(*data: object*)**           | Create an instance.                   | `Model.create({ name: 'Car', year: 2020});`
**update(*id, data: object*)**       | Update an instance by id.             | `Model.create(12, { name: 'Truck', year: 2021});`
**destroy(*id*)**                    | Delete an instance by id.             | `Model.destroy(12);`
