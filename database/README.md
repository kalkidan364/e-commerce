# ShopHub E-Commerce Database

## Overview
This directory contains the complete MySQL database schema for the ShopHub e-commerce platform.

## Files
- `schema.sql` - Complete database schema with tables, views, procedures, triggers, and default data

## Database Information
- **Database Name**: `shophub_ecommerce`
- **Character Set**: `utf8mb4`
- **Collation**: `utf8mb4_unicode_ci`
- **Engine**: InnoDB
- **MySQL Version**: 8.0+

## Installation

### Prerequisites
- MySQL 8.0 or higher installed
- MySQL client or MySQL Workbench

### Steps to Install

1. **Open MySQL Command Line or MySQL Workbench**

2. **Run the schema file**:
   ```bash
   mysql -u root -p < schema.sql
   ```

   Or in MySQL Workbench:
   - File → Open SQL Script
   - Select `schema.sql`
   - Execute the script

3. **Verify Installation**:
   ```sql
   USE shophub_ecommerce;
   SHOW TABLES;
   ```

## Database Structure

### Core Tables (24 tables)

#### User Management
- `users` - User accounts and authentication
- `addresses` - User shipping/billing addresses
- `activity_logs` - User activity tracking

#### Product Management
- `products` - Product catalog
- `product_images` - Product images
- `product_tags` - Product tags
- `categories` - Product categories

#### Shopping & Orders
- `carts` - Shopping carts
- `cart_items` - Cart items
- `orders` - Customer orders
- `order_items` - Order line items
- `order_addresses` - Order shipping/billing addresses

#### Payments
- `payments` - Payment transactions
- `coupons` - Discount coupons
- `coupon_usage` - Coupon usage tracking
- `shipping_methods` - Shipping options

#### Reviews & Engagement
- `reviews` - Product reviews
- `review_images` - Review images
- `wishlist` - User wishlists

#### System
- `notifications` - User notifications
- `newsletter_subscribers` - Email subscribers
- `contact_messages` - Contact form submissions
- `settings` - System settings
- `banners` - Homepage banners

## Default Data

### Admin User
- **Email**: `admin@shophub.com`
- **Password**: `Admin@123`
- **Role**: admin
- ⚠️ **IMPORTANT**: Change this password immediately after first login!

### Categories (12)
- Electronics
- Fashion
- Home & Kitchen
- Sports & Outdoors
- Books
- Toys & Games
- Beauty & Personal Care
- Health & Wellness
- Automotive
- Pet Supplies
- Office Products
- Garden & Outdoor

### Shipping Methods (4)
- Standard Shipping ($5.99)
- Express Shipping ($12.99)
- Next Day Delivery ($24.99)
- Free Shipping ($0.00)

### System Settings (10)
- Site name, email, phone
- Currency (USD)
- Tax rate (8.5%)
- Free shipping threshold ($50)
- Low stock threshold (10)
- Items per page (12)
- Feature toggles

## Database Features

### Views (3)
1. `vw_products_with_category` - Products with category details
2. `vw_order_summary` - Order summaries with customer info
3. `vw_user_statistics` - User statistics and metrics

### Stored Procedures (3)
1. `update_product_rating(product_id)` - Updates product rating from reviews
2. `process_order(...)` - Creates new order with order number
3. `update_stock_after_order(order_id)` - Updates product stock after order

### Triggers (4)
1. `update_cart_total_after_insert` - Updates cart total on item insert
2. `update_cart_total_after_update` - Updates cart total on item update
3. `update_cart_total_after_delete` - Updates cart total on item delete
4. `increment_coupon_usage` - Increments coupon usage count

## Indexes

All tables include appropriate indexes for:
- Primary keys
- Foreign keys
- Frequently queried columns
- Composite indexes for common queries
- Full-text search on products

## Security Considerations

1. **Change Default Password**: The default admin password must be changed
2. **Use Environment Variables**: Store database credentials in environment variables
3. **Limit Privileges**: Create separate database users with limited privileges
4. **Enable SSL**: Use SSL connections for production
5. **Regular Backups**: Implement automated backup strategy

## Backup & Restore

### Backup Database
```bash
mysqldump -u root -p shophub_ecommerce > backup_$(date +%Y%m%d).sql
```

### Restore Database
```bash
mysql -u root -p shophub_ecommerce < backup_20260205.sql
```

## Common Queries

### Get All Active Products
```sql
SELECT * FROM vw_products_with_category 
WHERE is_active = TRUE 
ORDER BY created_at DESC;
```

### Get User Order History
```sql
SELECT * FROM vw_order_summary 
WHERE user_id = 1 
ORDER BY created_at DESC;
```

### Get Low Stock Products
```sql
SELECT id, name, sku, stock, low_stock_threshold 
FROM products 
WHERE stock <= low_stock_threshold 
AND is_active = TRUE;
```

### Get Top Selling Products
```sql
SELECT id, name, sold_count, rating 
FROM products 
WHERE is_active = TRUE 
ORDER BY sold_count DESC 
LIMIT 10;
```

## Maintenance

### Optimize Tables
```sql
OPTIMIZE TABLE products, orders, order_items;
```

### Analyze Tables
```sql
ANALYZE TABLE products, orders, users;
```

### Check Table Status
```sql
SHOW TABLE STATUS FROM shophub_ecommerce;
```

## Troubleshooting

### Issue: Foreign Key Constraint Fails
**Solution**: Ensure parent records exist before inserting child records

### Issue: Duplicate Entry Error
**Solution**: Check UNIQUE constraints on email, slug, sku, code fields

### Issue: Trigger Not Working
**Solution**: Verify DELIMITER is properly set when creating triggers

## Support

For issues or questions:
- Check the main project documentation
- Review the schema comments
- Contact the development team

---

**Version**: 1.0.0  
**Last Updated**: February 5, 2026  
**Maintained By**: ShopHub Development Team
