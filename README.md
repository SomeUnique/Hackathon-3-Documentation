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

Day-3

1. Business Overview
1.1 Purpose
The purpose of this food website is to create an online platform where customers can:
 Browse a variety of food items, meals, or beverages.
 Place online orders for delivery or pickup.
 Track their orders in real-time.
1.2 Goals
 Provide a seamless food ordering experience.
 Ensure accurate and timely delivery of orders.
 Build customer loyalty through excellent service and user experience.

1.3 Target Audience
 Individuals aged 18-45.
 Office workers, students, and busy professionals looking for convenient food options.
 Food enthusiasts who want high-quality meals delivered to their doorstep.
1.4 Unique Selling Points
 Real-time order tracking.
 Curated menu with locally sourced ingredients.
 Integration with top-notch logistics providers for fast delivery.
 User-friendly interface with personalized recommendations.

3. Features and Functionality
   
2.1 User Features
1. Authentication
o Users can sign up, log in, and log out using Clerk.
o Social login options (Google, Facebook, etc.).
2. Food Menu
o View categorized food items (e.g., meals, beverages, desserts).
o Search and filter options (e.g., by cuisine, price, or dietary preferences).
3. Ordering System
o Add items to the cart.
o Modify quantities before checkout.
o Apply promo codes and discounts.
4. Payment Gateway
o Integration with payment providers (Stripe).
5. Order Tracking
o Real-time order tracking using ShipEngine.
o Notifications for order status (e.g., order confirmed, out for delivery).
6. Reviews and Ratings
o Users can rate their food and delivery experience.
o Option to leave feedback for continuous improvement.
2.2 Admin Features
1. Dashboard
o Manage menu items (add, update, delete).
o View and manage user accounts.
o Monitor order statuses.
2. Order Management
o View incoming orders in real time.
o Assign orders to delivery personnel.
3. Analytics and Reporting
o Sales data visualization.
o Customer feedback analysis.
o Track popular menu items.
3. Technical Overview
3.1 Tech Stack
 Frontend: React with Next.js and Tailwind CSS for styling.
 Backend: Next.js API routes and Sanity for content management.
 Database: Sanity for storing product details and user data.
 Authentication: Clerk for user management and secure login.
 Order Tracking: ShipEngine for real-time delivery updates.

3.2 APIs
1. Sanity CMS
o Manages food items, categories, and blog content.
o Fetch data using GROQ queries.
2. Clerk
o Handles user authentication, profile management, and session handling.
3. ShipEngine
o Provides shipping rates, label creation, and order tracking.
4. Stripe
o Facilitates secure online payments.
3.3 Database Structure
 User
o ID, Name, Email, Password, Address, Order History.
 Food Items
o ID, Name, Category, Price, Ingredients, Image URL.
 Orders
o Order ID, User ID, Food Items, Total Amount, Status.
 Delivery
o Order ID, Tracking Number, Status, Estimated Delivery Time.
4. Workflow
   
4.1 User Workflow
1. Sign-Up/Login: Users register or log in using Clerk.
2. Browse Menu: Explore food items from the categorized menu.
3. Place Order: Add items to the cart, confirm details, and make payment.
4. Order Confirmation: Receive confirmation via email or notification.
5. Track Order: Real-time updates via ShipEngine.
6. Delivery: Receive food and leave feedback.
4.2 Admin Workflow
1. Menu Management: Add or update food items in Sanity.
2. Order Processing: Approve and assign delivery using the admin dashboard.
3. Delivery Coordination: Use ShipEngine to track and manage deliveries.
4. Analytics Monitoring: Review performance metrics and customer feedback.
   
WorkFlow Diagram
[Frontend (Next.js)]
 |
[Sanity CMS] <-------> [Product Data API]
 |
[Third-Party APIs] ---> [Shipment Tracking API]
 |
 ---> [Payment Gateway]

Diagram
 LOG INS
 DISPLAY UI + CONTROL USER ACTION

 MANAGE PRODUCT, ORDER OR CUSTOMER DATA
 CONNECTED WITH
 
5. API Integration Steps
USER
CLERK LOG IN
RK
FOOD WEBSITE / FRONTEND
SANITY CMS THIRD PARTY APIS
ORDER DATA
SHIPMENT
PAYMENT
TRACKING
STRIPE SHIPENGINE
HANDLE SHIPMENT
TRACKING AND
PAYMENT METHOD
GET AND POST
DATA FROM
SANITY
INSERT PRODUCT DATA
IN SANITY

5.1 Sanity CMS
1. Create schemas for Food Items, Categories, and Orders.
2. Use GROQ queries to fetch data for the menu and blog
Schemas
Food Schema
export default {
name: 'food',
type: 'document',
title: 'Food',
fields: [
{
name: 'title',
type: 'string',
title: 'Food Title',
},
{
name: 'category',
type: 'string',
title: 'Category',
description:
'Category of the food item (e.g., Burger, Sandwich, Drink, etc.)',
},
{
name: 'price',
type: 'number',
title: 'Current Price',
},
{
name: 'rating',
type: 'number',
title: 'Rating',
description: 'Customers rating',
},
{
name: 'image',
type: 'image',
title: 'Food Image',
options: {
hotspot: true,
},
},
{
name: 'description',
type: 'text',
title: 'Description',
description: 'Short description of the food item',
},
{
name: "id",
type: "string",
title:"Id"
},
{
name: 'stock',
type: 'boolean',
title: 'Available',
description: 'Availability status of the food item',
},
],
};
Chef Schema
export default {
name: 'chef',
type: 'document',
title: 'Chef',
fields: [
{
name: 'name',
type: 'string',
title: 'Chef Name',
},
{
name: 'position',
type: 'string',
title: 'Position',
description: 'Role or title of the chef (e.g., Head Chef, Sous Chef)',
},
{
name: 'experience',
type: 'number',
title: 'Years of Experience',
description: 'Number of years the chef has worked in the culinary field',
},
{
name: 'specialty',
type: 'string',
title: 'Specialty',
description: 'Specialization of the chef (e.g., Italian Cuisine,
Pastry)',
},
{
name: 'image',
type: 'image',
title: 'Chef Image',
options: {
hotspot: true,
},
},
{
name: 'description',
type: 'text',
title: 'Description',
description: 'Short bio or introduction about the chef',
},
{
name: 'available',
type: 'boolean',
title: 'Currently Active',
description: 'Availability status of the chef',
},
],
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
};
GROQ Queries
Food
const query = `*[_type == "food"]{
_id,
title,
price,
"imageUrl": image.asset->url,
description,
rating,
review,
stock
}`;
const data: Product[] = await client.fetch(query);
Chef
const query = `*[_type=="chef"]{
_id,
name,
specialty,
"imageUrl":image.asset->url,
}`
const chef = await client.fetch(query)

5.2 Clerk Authentication
1. Install Clerk SDK.
2. Set up authentication routes for sign-up, login, and logout.
3. Restrict access to certain pages using Clerk middleware.
   
5.3 ShipEngine
1. Create a ShipEngine account.
2. Use API keys to integrate real-time order tracking.
3. Fetch delivery status and display it on the user's dashboard.
5.4 Stripe Payment
1. Create a Stripe account.
2. Set up payment intents for secure transactions.
3. Confirm payment status before order confirmation.
 title: 'Total Amount' },
 {
 name: 'status',
 type: 'string',
 title: 'Order Status' }
 ]

Day-4

Objective
Day 4 focused on designing and developing dynamic frontend components for the FoodTuck
marketplace. The goal was to fetch and display data dynamically using APIs or Sanity CMS and
ensure components are modular, reusable, and responsive.
Key Learning Outcomes
1. Developed dynamic frontend components to fetch and display marketplace data.
2. Designed reusable and modular components for scalability.
3. Improved understanding of state management techniques.
4. Applied responsive design principles for better user experience.
5. Followed professional workflows to mimic real-world development practices.
   
Components Developed
1. Product Listing Component
 Functionality: Displayed a grid of products dynamically fetched from the backend.
 Fields Included: Product Name, Price and Image.
 Example: Grid layout with product cards.
2. Product Detail Component
 Functionality: Created detailed pages for each product using dynamic routing.
 Fields Included: Description, Price, Available .
3. Category Component
 Functionality: Dynamically displayed product categories and enabled filtering.
4. Search Bar
 Functionality: Allowed users to search for products by name or id.
5. Cart Component
 Functionality: Displayed selected items, quantities, and total price.
 State Management: Tracked cart items using React Context.
6. Filter Panel Component
 Functionality: Allowed users to filter products by Category.
7. Responsive Header and Footer
 Functionality: Included navigation links, branding, and key contact details.
 Responsiveness: Adjusted design dynamically for desktop, tablet, and mobile views.
Frontend Best Practices Followed
1. Reusable Components
o Designed modular components like ProductCard and CategoryFilter to be
used across pages.
o Passed data via props for flexibility.
2. State Management
o Used React state and context for efficient data management.
3. Styling
o Implemented responsive designs using Tailwind CSS.
o Ensured consistency across desktop and mobile views.
4. Performance Optimization
o Lazy-loaded images and assets to improve load time.
o Implemented pagination for large datasets.
Challenges Faced
1. Dynamic Routing Issues:
o Initial challenges with setting up product detail pages using Next.js dynamic
routing.
o Solution: Reviewed and corrected file structure to enable correct routing.

3. API Data Fetching:
o Encountered delays in rendering data due to API response time.
o Solution: Used loading states to improve user experience.
4. Responsive Design Adjustments:
o Ensuring the UI adapted perfectly on smaller screens like the iPhone 12.
o Solution: Adjusted breakpoints in Tailwind CSS for seamless responsiveness.

Next Steps
1. Implement advanced features like wishlist and order tracking.
2. Optimize the search bar functionality for better performance.
3. Test components for cross-browser compatibility.
4. Document all steps and challenges for future reference.
   
Conclusion
Day 4 marked significant progress in creating a dynamic and professional frontend for the
FoodTuck marketplace. The components are now modular, scalable, and responsive, laying a
strong foundation for future development and real-world deployment.

Day-5

Overview
This report documents the testing, error handling, and backend refinement conducted for the
FoodTuck Q-Commerce marketplace. The goal was to ensure functionality, responsiveness, and
reliability of the platform, following professional testing standards.
Test Cases Executed

1. Product Listing Page Validation
 Test Case ID: TC001
 Steps: Open the products page and verify product display.
 Expected Result: Products should display successfully.
 Actual Result: Products displayed successfully.
 Severity Level: Low
 Remarks: No issues found.

3. API Error Handling
 Test Case ID: TC002
 Steps: Disconnect API > Refresh the page.
 Expected Result: Display an error message.
 Actual Result: Error message displayed.
 Severity Level: Low
 Remarks: Handled gracefully.

5. Cart Functionality
 Test Case ID: TC003
 Steps: Add items to the cart and navigate to the cart.
 Expected Result: Products should appear in the cart.
 Actual Result: Products displayed correctly.
 Severity Level: Medium
 Remarks: Working as intended.

6. Responsiveness on Mobile
 Test Case ID: TC004
 Steps: Inspect website using mobile device simulation.
 Expected Result: Content adjusts to the screen size.
 Actual Result: Content adjusts correctly.
 Severity Level: Medium
 Remarks: Responsive design confirmed.

8. Search Bar Validation
 Test Case ID: TC005
 Steps: Search for non-existent items.
 Expected Result: "No products found" dropdown should appear.
 Actual Result: Dropdown did not appear.
 Severity Level: High
 Remarks: Needs fixing to handle irrelevant search queries.

10. Dynamic Product Detail Pages
 Test Case ID: TC006
 Steps: Open a product card and validate its dynamic page.
 Expected Result: The correct product details page opens.
 Actual Result: Functions as expected.
 Severity Level: Low
 Remarks: No issues found.

12. Cross-Browser Compatibility
 Test Case ID: TC007
 Steps: Open the website on Chrome, Firefox, and Microsoft Edge.
 Expected Result: Consistent functionality and layout.
 Actual Result: Worked seamlessly across all tested browsers.
 Severity Level: Low
 Remarks: No issues found.

Performance Optimization
 Tools Used: Lighthouse, Pagespeed
 Steps Taken:
1. Compressed images using TinyPNG.
2. Implemented lazy loading for assets.
3. Reduced unused CSS and JavaScript.
4. Enabled browser caching for faster repeat visits.

Error Handling
 API Failures: Used try-catch blocks to manage errors.
 Fallback UI: Displayed user-friendly messages (e.g., "error creating Order"").
 Examples:
 try{ 
 await client.create (orderData) 
 localStorage.removeItem("appliedDiscount") 
 } 
 catch(error){ 
 console.error("error creating Order", error) 
 }

Cross-Browser and Device Testing
 Browsers Tested: Chrome, Firefox, Safari, Edge.
 Devices Tested: Desktop, tablet, iPhone 12.
 Results:
 Fully responsive across all tested devices and browsers.
 No layout issues observed.

Security Measures
Input fields validated to prevent injection attacks.
HTTPS enabled for secure communication.
API keys stored in environment variables.
Tools Used: OWASP ZAP, Burp Suite.

Challenges Faced
1. Search bar functionality failed to display "Not showing Select Category"
o Resolution: To be fixed in the next sprint.

Conclusion
The FoodTuck website passed most functional and non-functional testing parameters, with the
exception of the search bar issue. It is now optimized for performance and responsive design,
ready for real-world deployment after resolving the identified issues.

Next Steps
1. Fix the search bar dropdown issue.
2. Conduct additional user acceptance testing (UAT) with real users.
3. Re-test after implementing fixes.
   
Attachments:
https://pagespeed.web.dev/analysis/https-market-place-hackathon-builder-3
6uar-vercel-app/qy5qstp62e?form_factor=mobile 

Day-6







