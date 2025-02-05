# Hackathon-3-Documentation
From day-1 of hackathon 3 till day-7 of hackathon all documents are here .
Day 2:
Day 2 Task

Introduction:
This document outlines the technical foundation for your food business marketplace. The focus is
on defining the system architecture, workflows, API requirements, and Sanity CMS schema. The
goal is to ensure a seamless integration of frontend and backend components, enabling efficient
and scalable operations.

1.Define Technical Requirements:
Frontend Requirement
 Responsive Design:
o Ensure the marketplace works seamlessly on mobile and desktop devices.
 Essential Pages:
o Home
o Menu
o Blog
o About
o Shop
o Products/id {dynamic page}
o Sing In
o Sing Up
o Contact
o Checkout
o Order Confirmation
Backend Requirements (Sanity CMS):
 Use Sanity CMS for managing:
o Product data
o Customer details
o Order records
 Define schemas in Sanity to align with:
o Product structure (e.g., name, price, stock)
o Order structure (e.g., customer info, product details, payment status)
Third-Party API’s
 Shipment Tracking API:
o Fetch and display order shipment status in real-time.
 Payment Gateway API:
o Securely process payments and return confirmations to the system.
2. Design System Architecture
High-Level Architecture Diagram
[Frontend (Next.js)]
 |
[Sanity CMS] <-------> [Product Data API]
 |
[Third-Party APIs] ---> [Shipment Tracking API]
 |
 ---> [Payment Gateway]
Workflow Description
1. User Browsing Products:
o User visits the frontend (Next.js).
o Frontend requests product data via the Sanity CMS API.
o Products are dynamically displayed to the user.
2. Order Placement:
o User adds products to the cart and proceeds to checkout.
o Order details are sent to Sanity CMS for record-keeping.
o Payment is processed through the Payment Gateway.
3. Shipment Tracking:
o Order status is updated using the Shipment Tracking API.
o Real-time tracking information is displayed to the user.
5. Sanity CMS Schemas
Product Schema
export default {
 name: 'product',
 type: 'document',
 fields: [
 { name: 'name',
 type: 'string',
 title: 'Product Name'
},
 { name: 'price',
 type: 'number',
 title: 'Price'
},
 { name: 'stock',
 type: 'number',
 title: 'Stock Level'
},
 { name: 'image',
 type: 'image',
 title: 'Product Image'
}
 ]
};
Order Schema
export default {
 name: 'order',
 type: 'document',
 fields: [
 { name: 'customer',
 type: 'reference',
 to: [
 { type: 'customer' }],
 title: 'Customer'
},
 { name: 'products',
 type: 'array',
 of: [
 { type: 'reference',
 to: [
 { type: 'product' }
]
}],
title: 'Products' },
 { name: 'totalAmount',
 type: 'number',
 title: 'Total Amount' },
 {
 name: 'status',
 type: 'string',
 title: 'Order Status' }
 ]
