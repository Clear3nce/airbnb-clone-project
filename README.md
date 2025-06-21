# Frontend Answers.

## UI/UX Design Planning.

### Project overview

- This project is a full-stack clone of the popular accommodation booking platform Airbnb. The goal is to build a functional web application that allows users to browse property listings, view detailed property information, and complete bookings. The project will cover frontend development, backend APIs, database design, and deployment.


### Tech Stack
- Frontend: HTML, CSS, JavaScript (React or similar framework)
- Version Control: Git and GitHub
- Design Tools: Figma for UI/UX design


### Design goals and the key features that need to be implemented.

- Maintain visual consistency.
- Ensure fast loading times.
- Prioritize mobile responsiveness.
- Create an intuitive booking flow.

### Key features.

- Property search and filtering.
- Detailed property viewing
- Secure checkout process
- User authentication

### Primary pages.

- Property Listing View: grid display of available properties with filters.
- Listing Detailed View: Complete property details with images and booking form.
- Simple Checkout View: Streamlined payment and booking confirmation.

### Importance of User-Friendly Design.
- A well-designed booking system reduces friction in the user journey, increases conversion rates, and improves customer satisfaction. Clear navigation, intuitive interfaces, and responsive design are critical for success.


### Color Styles:

Primary: #FF5A5F
Secondary: #008489
Background: #FFFFFF
Text: #222222
Secondary Text: #717171

### Typography:

Primary Font: Circular, Medium (500), 16px
Headings: Circular, Bold (700), 24px-32px
Secondary Text: Circular, Book (400), 14px

### Importance of identifying design properties of a mock-up design is:
 1. Effective communication, aligning stakeholders.
 2. early Problem detection, minimising costly errors later in the development.
 3. Building design confidence.

## Project Roles and Responsibilities.

1. Project Manager ->	Oversees timeline, coordinates team, manages deliverables.
2. Frontend Developers ->	Implements UI components, ensures responsive design.
3. Backend Developers	-> Builds APIs, manages database, implements business logic.
4. Designers ->	Creates mockups, maintains design system, ensures UX quality.
5. QA/Testers ->	Writes test cases, performs testing, reports bugs.
6. DevOps Engineers ->	Manages deployment, CI/CD pipeline, server infrastructure.
7. Product Owner ->	Defines requirements, prioritizes features, represents stakeholders.
8. Scrum Master ->	Facilitates agile processes, removes blockers, organizes meetings.

## UI Component Patterns.

### Planned Components.
Navbar

- Logo
- Search bar
- User navigation
- Responsive menu
  
Property Card

- Property image
- Basic details (price, location, rating)
- Favorite button
- Responsive layout
  
Footer

- Site links
- Company information
- Social media links
- Copyright information

  Each component will be designed for reusability and consistency across the application.


# Answers for Backend (BE)

## Provide a brief overview of the project, including the project goals and the tech stack.
### This project is designed to simulate the development of a robust booking platform like Airbnb. It involves a deep dive into full-stack development, focusing on backend systems, database design, API development, and application security.
### Project goals:

  1. Develop an understanding of integrating technologies like Django, MySQL, and GraphQL in a unified ecosystem.
  2. User Management: Implement a secure system for user registration, authentication, and profile management.
  3. Property Management: Develop features for property listing creation, updates, and retrieval.
  4. Booking System: Create a booking mechanism for users to reserve properties and manage booking details.
  5. Payment Processing: Integrate a payment system to handle transactions and record payment details.
  6. Review System: Allow users to leave reviews and ratings for properties.
  7. Data Optimization: Ensure efficient data retrieval and storage through database optimizations.
 
### Tech stack:
- Python, Django, Database system e.g(MySQL), Docker, Github Actions.


## Team Roles and Responsibilities.
1. A business analyst -> Understands the customer’s business processes, translates the customer's business needs into requirements.
2. Database Administrator: Manages database design, indexing, and optimizations.
3. A product owner -> holds responsibility for a product vision and evolution,  Make sure the final product meets customer requirements.
4. A project manager -> makes sure a product or its part is delivered on time and within budget, manages and motivates the software development team.
5. A UI/UX designer -> Transforms a product vision into user-friendly designs
6. A software architect -> Designs a high-level software architecture, selects appropriate tools and platforms to implement the product vision
7. Software developers -> Engineers, and stabilizes the product.
8. Quality assurance engineers -> Makes sure an application performs according to requirements.
9. Test automation engineers -> Design a test automation ecosystem.
10. DevOps engineer -> Facilitates cooperation between development and operations teams.


## Technology Stack.
- Django: A high-level Python web framework used for building the RESTful API.
- Django REST Framework: Provides tools for creating and managing RESTful APIs.
- PostgreSQL: A powerful relational database used for data storage.
- GraphQL: Allows for flexible and efficient querying of data.
- Celery: For handling asynchronous tasks such as sending notifications or processing payments.
- Redis: Used for caching and session management.
- Docker: Containerization tool for consistent development and deployment environments.
- CI/CD Pipelines: Automated pipelines for testing and deploying code changes.

## Database Design.

###  Users
- `id` (Primary Key)
- `name`
- `email` (Unique)
- `password_hash`
#### A **User** can have multiple **Bookings** (one-to-many relationship)
  
###  properties
- `price_per_night`
- `host_id` (Foreign Key to Users)
- `location`
#### A **Property** can have multiple **Reviews** (one-to-many)
  
###  Bookings
- `check_in_date`
- `check_out_date`
- `total_price`
#### A **Booking** belongs to one **Property** and one **User** (the guest) (many-to-one relationships)

  
###  Reviews
- `rating`
- `comment`
- `created_at`
#### A **Review** belongs to one **Property** and one **User** (many-to-one)
  
###  Payments.
- `amount`
- `payment_method`
- `status`
- `transaction_date`
####  A **Payment** is associated with one **Booking** (one-to-one)



## Feature Breakdown.
###  API Documentation
- OpenAPI Standard: The backend APIs are documented using the OpenAPI standard to ensure clarity and ease of integration.
- Django REST Framework: Provides a comprehensive RESTful API for handling CRUD operations on user and property data.
- GraphQL: Offers a flexible and efficient query mechanism for interacting with the backend.

### User Authentication
Features: Register new users, authenticate, and manage user profiles.

### Property Management
Features: Create, update, retrieve, and delete property listings.

### Booking System
Features: Make, update, and manage bookings, including check-in and check-out details.

### Payment Processing
Features: Handle payment transactions related to bookings.

### Review System
Features: Post and manage reviews for properties.

### Database Optimizations
Indexing: Implement indexes for fast retrieval of frequently accessed data.
Caching: Use caching strategies to reduce database load and improve performance.

## API Security
### Authentication

- JWT (JSON Web Tokens) for user login/session management.

- Secure password storage using bcrypt (hashing + salting).

#### Why it matters: Ensures only verified users can access protected endpoints.

### Authorization (Role-Based Access Control - RBAC)

- Different permissions for guests, hosts, and admins.

- Middleware to validate user roles before allowing actions (e.g., only hosts can edit their properties).

#### Why it matters: Prevents users from accessing/modifying data they shouldn’t (e.g., a guest deleting a property).

### Rate Limiting

- Express-rate-limit to restrict excessive API calls (e.g., 100 requests/minute per IP).

#### Why it matters: Protects against brute-force attacks and DDoS attempts.

### Data Validation & Sanitization

- Express-validator to sanitize user inputs (e.g., preventing SQL injection).

#### Why it matters: Blocks malicious payloads from compromising the database.

### HTTPS & Secure Headers

- Enforce HTTPS via Helmet.js (sets security headers like X-Content-Type-Options).

#### Why it matters: Encrypts data in transit and mitigates XSS/clickjacking risks.

### Payment Security

- PCI DSS compliance (never store raw card details; use Stripe/PayPal tokens).

#### Why it matters: Prevents financial fraud and protects sensitive payment data.

### Logging & Monitoring

- Track suspicious activity (e.g., failed logins) using Winston/Morgan.

#### Why it matters: Early detection of breaches or abuse.

## CI/CD Pipeline.

### CI/CD (Continuous Integration and Continuous Deployment) automates the process of testing, building, and deploying code changes. This ensures faster, more reliable software delivery with fewer errors.
- Continuous Integration (CI):
Automatically runs tests and checks whenever code is pushed to the repository (e.g., on git push).
- Continuous Deployment (CD):
Automatically deploys the tested code to production/staging environments if all checks pass.

### Why It Matters for This Project

- Faster Development:
Catch bugs early with automated testing (e.g., unit/integration tests).

- Consistency:
Avoid "it works on my machine" issues by using standardized environments (e.g., Docker).

- Reliability:
Reduce manual errors in deployment (e.g., scripts handle builds + deployments).

- Scalability:
Easily roll back if a deployment fails.

### Tools We’ll Use

- GitHub Actions: For CI/CD workflows (runs tests on every push/pull request).

- Docker: Containerization to ensure consistent environments across development/staging/production.

- AWS/Heroku: For deployment automation (e.g., deploy to AWS Elastic Beanstalk after tests pass).










