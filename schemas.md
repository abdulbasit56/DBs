# Model Schemas

## `brand.js`
```javascript
import mongoose from 'mongoose';

const brandSchema = new mongoose.Schema({
  name: {
    type: String,
    required: true,
  },
  status: {
    type: String,
    enum: ['Active', 'Inactive'],
    default: 'Active',
  },
  image: {
    type: String,
  },
  createdBy: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'User',
  },
}, {
  timestamps: true,
});

const Brand = mongoose.model('Brand', brandSchema);

export default Brand;
```

## `category.js`
```javascript
import mongoose from 'mongoose';

const categorySchema = new mongoose.Schema({
  name: {
    type: String,
    required: true,
  },
  status: {
    type: String,
    enum: ['Active', 'Inactive'],
    default: 'Active',
  },
  image: {
    type: String,
  },
  createdBy: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'User',
  },
}, {
  timestamps: true,
});

const Category = mongoose.model('Category', categorySchema);

export default Category;
```

## `customer.js`
```javascript
import mongoose from 'mongoose';

const customerSchema = new mongoose.Schema({
  name: {
    type: String,
    required: true,
  },
  email: {
    type: String,
  },
  phone: {
    type: String,
  },
  address: {
    type: String,
  },
  city: {
    type: String,
  },
  country: {
    type: String,
  },
  image: {
    type: String,
  },
  status: {
    type: String,
    enum: ['Active', 'Inactive'],
    default: 'Active',
  },
  createdBy: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'User',
    required: true,
  },
}, {
  timestamps: true,
});

const Customer = mongoose.model('Customer', customerSchema);

export default Customer;
```

## `inventory.js`
```javascript
import mongoose from 'mongoose';

const inventorySchema = new mongoose.Schema({
  variant: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'ProductVariant',
    required: true,
  },
  store: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'Store',
    required: true,
  },
  qty: {
    type: Number,
    default: 0,
  },
  quantityAlert: {
    type: Number,
    default: 0,
  },
}, {
  timestamps: true,
});

const Inventory = mongoose.model('Inventory', inventorySchema);

export default Inventory;
```

## `orderItem.js`
```javascript
import mongoose from 'mongoose';

const orderItemSchema = new mongoose.Schema({
  sale: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'Sale',
  },
  product: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'Product',
    required: true,
  },
  variant: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'ProductVariant',
  },
  quantity: {
    type: Number,
    required: true,
  },
  unit_price: {
    type: Number,
    required: true,
  },
  discount: {
    type: Number,
    default: 0,
  },
  subtotal: {
    type: Number,
    required: true,
  },
}, {
  timestamps: true,
});

const OrderItem = mongoose.model('OrderItem', orderItemSchema);

export default OrderItem;
```

## `product.js`
```javascript
import mongoose from 'mongoose';

const productSchema = new mongoose.Schema({
  name: {
    type: String,
    required: true,
  },
  description: {
    type: String,
  },
  status: {
    type: String,
    enum: ['Active', 'Inactive'],
    default: 'Active',
  },
  image: {
    type: String,
  },
  slug: {
    type: String,
  },
  sellingType: {
    type: String,
    enum: ['Online', 'POS'],
  },
  productType: {
    type: String,
    enum: ['single', 'variable'],
    required: true,
  },
  taxType: {
    type: String,
    enum: ['Exclusive', 'Inclusive'],
  },
  tax: {
    type: Number,
  },
  discountType: {
    type: String,
    enum: ['Percentage', 'Fixed'],
  },
  discountValue: {
    type: Number,
  },
  warranties: {
    type: String,
  },
  barcodeSymbology: {
    type: String,
  },
  createdBy: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'User',
  },
  category: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'Category',
  },
  subCategory: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'SubCategory',
  },
  brand: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'Brand',
  },
  unit: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'Unit',
  },
  supplier: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'Supplier',
  },
  isLocked: {
    type: Boolean,
    default: false,
  },
  lockedAt: {
    type: Date,
  },
  lockedBy: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'User',
  },
});

const Product = mongoose.model('Product', productSchema);

export default Product;
```

## `productVariant.js`
```javascript
import mongoose from 'mongoose';

const productVariantSchema = new mongoose.Schema({
  sku: {
    type: String,
  },
  itemBarcode: {
    type: String,
  },
  price: {
    type: Number,
  },
  cost: {
    type: Number,
    default: 0.00,
  },
  weight: {
    type: Number,
    default: 0.00,
  },
  attributes: {
    type: mongoose.Schema.Types.Mixed,
  },
  expiryDate: {
    type: Date,
  },
  manufacturedDate: {
    type: Date,
  },
  product: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'Product',
    required: true,
  },
  createdBy: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'User',
    required: true,
  },
}, {
  timestamps: true,
});

const ProductVariant = mongoose.model('ProductVariant', productVariantSchema);

export default ProductVariant;
```

## `purchase.js`
```javascript
import mongoose from 'mongoose';

const purchaseSchema = new mongoose.Schema({
  reference: {
    type: String,
  },
  date: {
    type: Date,
  },
  status: {
    type: String,
  },
  payment_status: {
    type: String,
    enum: ['Paid', 'Unpaid', 'Overdue'],
  },
  total: {
    type: Number,
  },
  paid: {
    type: Number,
  },
  due: {
    type: Number,
  },
  supplier: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'Supplier',
  },
  items: [{
    type: mongoose.Schema.Types.ObjectId,
    ref: 'PurchaseItem'
  }],
  createdBy: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'User',
    required: true,
  },
}, {
  timestamps: true,
});

const Purchase = mongoose.model('Purchase', purchaseSchema);

export default Purchase;
```

## `purchaseItem.js`
```javascript
import mongoose from 'mongoose';

const purchaseItemSchema = new mongoose.Schema({
  purchase: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'Purchase',
    required: true,
  },
  product: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'Product',
    required: true,
  },
  quantity: {
    type: Number,
    required: true,
  },
  unitPrice: {
    type: Number,
    required: true,
  },
  discount: {
    type: Number,
    default: 0,
  },
  subtotal: {
    type: Number,
    required: true,
  },
}, {
  timestamps: true,
});

const PurchaseItem = mongoose.model('PurchaseItem', purchaseItemSchema);

export default PurchaseItem;
```

## `report.js`
```javascript
import mongoose from 'mongoose';

const reportSchema = new mongoose.Schema({
  type: {
    type: String,
  },
  reference: {
    type: String,
  },
  date: {
    type: Date,
  },
  amount: {
    type: Number,
  },
  payment_method: {
    type: String,
  },
  payment_status: {
    type: String,
  },
  customer_name: {
    type: String,
  },
  customer_image: {
    type: String,
  },
  product_name: {
    type: String,
  },
  product_image: {
    type: String,
  },
  category: {
    type: String,
  },
}, {
  timestamps: true,
});

const Report = mongoose.model('Report', reportSchema);

export default Report;
```

## `returnItems.js`
```javascript
import mongoose from 'mongoose';

const returnItemSchema = new mongoose.Schema({
  saleReturn: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'SaleReturn',
    required: true,
  },
  product: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'Product',
    required: true,
  },
  quantity: {
    type: Number,
    required: true,
  },
  unitPrice: {
    type: Number,
    required: true,
  },
  reason: {
    type: String,
  },
  subtotal: {
    type: Number,
    required: true,
  },
}, {
  timestamps: true,
});

const ReturnItem = mongoose.model('ReturnItem', returnItemSchema);

export default ReturnItem;
```

## `sale.js`
```javascript
import mongoose from 'mongoose';

const saleSchema = new mongoose.Schema({
  reference: {
    type: String,
  },
  date: {
    type: Date,
  },
  status: {
    type: String,
    enum: ['Completed', 'Pending'],
  },
  payment_status: {
    type: String,
    enum: ['Paid', 'Unpaid', 'Overdue'],
  },
  payment_method: {
    type: String,
  },
  subtotal: {
    type: Number,
  },
  discount: {
    type: Number,
  },
  tax: {
    type: Number,
  },
  shipping: {
    type: Number,
  },
  total: {
    type: Number,
  },
  paid: {
    type: Number,
  },
  due: {
    type: Number,
  },
  note: {
    type: String,
  },
  customer: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'Customer',
  },
  user: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'User',
  },
  store: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'Store',
    required: true,
  },
  items: [{
    type: mongoose.Schema.Types.ObjectId,
    ref: 'OrderItem',
  }],
}, {
  timestamps: true,
});

const Sale = mongoose.model('Sale', saleSchema);

export default Sale;
```

## `saleReturn.js`
```javascript
import mongoose from 'mongoose';

const saleReturnSchema = new mongoose.Schema({
  reference: {
    type: String,
  },
  date: {
    type: Date,
  },
  status: {
    type: String,
    enum: ['Pending', 'Completed'], // Guessing based on sale.js
    default: 'Pending',
  },
  total: {
    type: Number,
    required: true,
  },
  paid: {
    type: Number,
    default: 0,
  },
  due: {
    type: Number,
  },
  payment_status: {
    type: String,
    enum: ['Paid', 'Unpaid', 'Partial'], // Guessing
    default: 'Unpaid',
  },
  customer: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'Customer',
    required: true,
  },
  sale: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'Sale',
    required: true,
  },
  store: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'Store',
    required: true,
  },
  items: [{
    type: mongoose.Schema.Types.ObjectId,
    ref: 'ReturnItem',
  }],
  createdBy: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'User',
    required: true,
  },
}, {
  timestamps: true,
});

const SaleReturn = mongoose.model('SaleReturn', saleReturnSchema);

export default SaleReturn;
```

## `store.js`
```javascript
import mongoose from 'mongoose';

const storeSchema = new mongoose.Schema({
  name: {
    type: String,
    required: true,
  },
  address: {
    type: String,
  },
  status: {
    type: String,
    enum: ['Active', 'Inactive'],
    default: 'Active',
  },
  createdBy: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'User',
    required: true,
  },
}, {
  timestamps: true,
});

const Store = mongoose.model('Store', storeSchema);

export default Store;
```

## `subCategory.js`
```javascript
import mongoose from 'mongoose';

const subCategorySchema = new mongoose.Schema({
  name: {
    type: String,
    required: true,
  },
  status: {
    type: String,
    enum: ['Active', 'Inactive'],
    default: 'Active',
  },
  category: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'Category',
    required: true,
  },
  createdBy: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'User',
    required: true,
  },
}, {
  timestamps: true,
});

const SubCategory = mongoose.model('SubCategory', subCategorySchema);

export default SubCategory;
```

## `supplier.js`
```javascript
import mongoose from 'mongoose';

const supplierSchema = new mongoose.Schema({
  name: {
    type: String,
    required: true,
  },
  email: {
    type: String,
  },
  phone: {
    type: String,
  },
  address: {
    type: String,
  },
  image: {
    type: String,
  },
  status: {
    type: String,
    enum: ['Active', 'Inactive'],
    default: 'Active',
  },
  createdBy: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'User',
    required: true,
  },
}, {
  timestamps: true,
});

const Supplier = mongoose.model('Supplier', supplierSchema);

export default Supplier;
```

## `unit.js`
```javascript
import mongoose from 'mongoose';

const unitSchema = new mongoose.Schema({
  name: {
    type: String,
    required: true,
  },
  short_name: {
    type: String,
  },
  status: {
    type: String,
    enum: ['Active', 'Inactive'],
    default: 'Active',
  },
  createdBy: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'User',
  },
}, {
  timestamps: true,
});

const Unit = mongoose.model('Unit', unitSchema);

export default Unit;
```

## `user.js`
```javascript
import mongoose from 'mongoose';

const userSchema = new mongoose.Schema({
  name: {
    type: String,
    required: true,
  },
  email: {
    type: String,
    required: true,
    unique: true,
  },
  role: {
    type: String,
    enum: ['admin', 'biller'],
    default: 'biller',
  },
  status: {
    type: String,
    enum: ['Active', 'Inactive'],
    default: 'Active',
  },
  password: {
    type: String,
    required: true,
  },
}, {
  timestamps: true,
});

const User = mongoose.model('User', userSchema);

export default User;
```

## `warehouse.js`
```javascript
import mongoose from 'mongoose';

const warehouseSchema = new mongoose.Schema({
  name: {
    type: String,
    required: true,
  },
  address: {
    type: String,
  },
  status: {
    type: String,
    enum: ['Active', 'Inactive'],
    default: 'Active',
  },
  createdBy: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'User',
    required: true,
  },
}, {
  timestamps: true,
});

const Warehouse = mongoose.model('Warehouse', warehouseSchema);

export default Warehouse;
```
