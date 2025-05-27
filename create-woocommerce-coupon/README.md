# WooCommerce Coupon Creation Workflow

This workflow automates the creation of WooCommerce coupons with customizable parameters. It's designed to be triggered by other workflows and provides a flexible way to generate and manage discount coupons in your WooCommerce store.

## Main Use Cases

1. **Automated Coupon Generation**
   - Create coupons with automatically generated unique codes (prefixed with "AMY")
   - Set up discounts with various types (percentage, fixed cart, fixed product)
   - Configure free shipping options

2. **Flexible Discount Configuration**
   - Set specific discount amounts
   - Define usage limits (per coupon and per user)
   - Restrict coupons to specific products or exclude certain products
   - Set minimum and maximum order amounts
   - Add email restrictions for targeted promotions

3. **Integration Capabilities**
   - Can be triggered by other workflows
   - Seamless integration with WooCommerce REST API
   - Supports both automated and manual coupon creation

## How It Works

1. **Trigger**
   - The workflow is triggered by another workflow
   - Accepts various input parameters for coupon configuration

2. **Code Processing**
   - Generates a unique coupon code with "AMY" prefix
   - Applies default values if not specified:
     - Discount type: fixed_cart
     - Individual use: false
     - Free shipping: true
     - Exclude sale items: false

3. **Validation**
   - Checks for required fields (amount and code)
   - Ensures all values are properly formatted
   - Removes null or empty values from the request

4. **Coupon Creation**
   - Makes a POST request to WooCommerce API
   - Creates the coupon with specified parameters
   - Returns the created coupon details

## Input Parameters

The workflow accepts the following parameters:

- `code`: Coupon code (optional, auto-generated if not provided)
- `amount`: Discount amount
- `discount_type`: Type of discount (percent, fixed_cart, fixed_product)
- `description`: Coupon description
- `date_expires`: Expiration date
- `individual_use`: Whether coupon can be used in conjunction with other coupons
- `product_ids`: Specific products the coupon can be used for
- `excluded_product_ids`: Products excluded from the coupon
- `usage_limit`: Maximum number of times the coupon can be used
- `usage_limit_per_user`: Maximum number of times the coupon can be used per user
- `limit_usage_to_x_items`: Maximum number of items the coupon can be applied to
- `minimum_amount`: Minimum order amount required
- `maximum_amount`: Maximum order amount allowed
- `email_restrictions`: List of email addresses that can use the coupon

## Requirements

- WooCommerce REST API access
- Valid WooCommerce API credentials
- Proper permissions to create coupons

## Notes

- The workflow automatically generates coupon codes with an "AMY" prefix
- All amounts should be provided as strings
- The workflow includes error handling and will continue even if some parameters are missing 