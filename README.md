# Asto Gear - Computer Accessories E-commerce Platform

🌐 **Live Demo:** [astogear.com](https://astogear.com)

---

## Full Demo Video

[Watch the complete walkthrough on YouTube](https://www.youtube.com/watch?v=LKBMF5jg0k8)

---

## 📺 Demo

### Authentication
![User Authentication](authentication.gif)

### Homepage & Product Browsing
![Homepage and Product Browsing](homepage_productBrows.gif)

### Product Details
![Product Detail Page](product_detail.gif)

### Shopping Cart & Checkout
![Checkout Process](checkout_payment.gif)

### Payment Integration
![Bakong KHQR Payment](checkout_payment.gif)

### Real-time Notifications
![WebSocket Real-time Notifications](real_time_notification.gif)

### Seller Dashboard
![Admin Dashboard](seller_dashboard.gif)

---

## System Architecture

```mermaid
graph TB
    subgraph CDN["CDN Layer"]
        CLOUDFLARE[Cloudflare CDN<br/>SSL/TLS & DDoS Protection]
    end

    subgraph HOST["Host Server"]
        NGINX_PROXY[Nginx Reverse Proxy<br/>HTTP/HTTPS<br/>Load Balancer]
    end

    subgraph CLIENT["Client Layer"]
        USER[Users - Web & Mobile Browsers]
    end

    subgraph PRESENTATION["Presentation Layer"]
        direction LR
        REACT[React + Vite + Tailwind CSS]
        FEATURES[Multi-Language Support<br/>Real-time Notifications<br/>Shopping Cart System]
    end

    subgraph APPLICATION["Application Layer"]
        direction TB
        
        subgraph API_GATEWAY["API Gateway"]
            EXPRESS[Express.js REST API]
            WS[WebSocket Server]
        end
        
        subgraph SECURITY["Security Layer"]
            JWT[JWT Authentication]
            AUTHZ[Authorization Middleware]
        end
        
        subgraph CONTROLLERS["Controllers"]
            direction LR
            C1[Auth]
            C2[Products]
            C3[Orders]
            C4[Payments]
            C5[Users]
        end
    end

    subgraph DATA["Data Layer"]
        direction TB
        DB[(MySQL Database<br/>Sequelize ORM)]
        
        TABLES[Tables: users, products, orders<br/>payments, categories, brands<br/>addresses, notifications]
    end

    subgraph SERVICES["External Services"]
        direction LR
        FIREBASE[Firebase<br/>Google OAuth]
        CLOUDINARY[Cloudinary<br/>Image Storage]
        BAKONG[Bakong API<br/>KHQR Payment]
    end

    subgraph INFRASTRUCTURE["Docker Infrastructure"]
        direction LR
        C_FRONT[Frontend Container<br/>Nginx Alpine]
        C_BACK[Backend Container<br/>Node.js 18]
        C_DB[MySQL Container<br/>MySQL 5.7/8.0]
    end

    subgraph DEPLOYMENT["Deployment & Migration"]
        direction LR
        PROD[Production Server] --> BACKUP[Backup & Migrate] --> STAGING[Staging Server]
    end

    %% Main flow connections
    USER --> CLOUDFLARE
    CLOUDFLARE --> NGINX_PROXY
    NGINX_PROXY --> C_FRONT
    NGINX_PROXY --> C_BACK
    
    C_FRONT --> REACT
    REACT <--> EXPRESS
    REACT <--> WS
    
    EXPRESS --> JWT
    JWT --> AUTHZ
    AUTHZ --> CONTROLLERS
    
    CONTROLLERS --> DB
    DB --> TABLES
    
    CONTROLLERS --> SERVICES
    
    %% Docker connections
    C_FRONT -.contains.- REACT
    C_BACK -.contains.- EXPRESS
    C_BACK -.contains.- WS
    C_DB -.contains.- DB
    
    %% Styling with professional dark green theme
    classDef cdnStyle fill:#ff6b35,stroke:#f7931e,stroke-width:3px,color:#ffffff
    classDef hostStyle fill:#2c3e50,stroke:#3498db,stroke-width:3px,color:#ffffff
    classDef clientStyle fill:#1a1a1a,stroke:#00ff88,stroke-width:3px,color:#ffffff
    classDef frontendStyle fill:#0d7377,stroke:#14ffec,stroke-width:3px,color:#ffffff
    classDef backendStyle fill:#212121,stroke:#4caf50,stroke-width:3px,color:#ffffff
    classDef dataStyle fill:#1b5e20,stroke:#76ff03,stroke-width:3px,color:#ffffff
    classDef serviceStyle fill:#004d40,stroke:#00e676,stroke-width:3px,color:#ffffff
    classDef infraStyle fill:#263238,stroke:#69f0ae,stroke-width:3px,color:#ffffff
    classDef deployStyle fill:#1b5e20,stroke:#00e676,stroke-width:3px,color:#ffffff
    
    class CDN,CLOUDFLARE cdnStyle
    class HOST,NGINX_PROXY hostStyle
    class CLIENT,USER clientStyle
    class PRESENTATION,REACT,FEATURES frontendStyle
    class APPLICATION,EXPRESS,WS,SECURITY,JWT,AUTHZ,API_GATEWAY,CONTROLLERS,C1,C2,C3,C4,C5 backendStyle
    class DATA,DB,TABLES dataStyle
    class SERVICES,FIREBASE,CLOUDINARY,BAKONG serviceStyle
    class INFRASTRUCTURE,C_FRONT,C_BACK,C_DB infraStyle
    class DEPLOYMENT,PROD,BACKUP,STAGING deployStyle
```

The diagram above illustrates the complete system architecture of Asto Gear, showing the flow from users through CDN and reverse proxy layers, to the containerized application services, database, and external API integrations.

---

## Project Overview

**Asto Gear** is a full-stack e-commerce web application that allows users to build and purchase computer accessories with ease. The platform features real-time notifications, multi-language support, and integrated payment through Bakong API. All orders come with **free delivery** for users.

---

## Key Features

### Authentication
- User registration and login (manual or Google OAuth)
- JWT-based authentication with cookies and authorization headers
- Secure session management

### E-commerce Functionality
- Browse computer accessories and components
- Search products by name
- Filter products by brand and category
- Add products to shopping cart
- View order receipts

### Seller Dashboard
- Full CRUD operations for products, brands, and categories
- Track user login/signup activity
- Manage product inventory

### Real-time Features
- WebSocket notifications for order updates
- Live order tracking

### Payment Integration
- Bakong KHQR payment gateway
- Secure payment processing

### Multi-language Support
- Language options: Khmer, Chinese, English
- Flag-based language switcher

### Delivery Management
- User input for phone number and address
- Multiple delivery provider options:
  - JNT Express
  - Vireak Buntham
  - Grab

### Contact & Support
- About Us page
- Contact via Telegram, Facebook, and Instagram

---

## Tech Stack

### Backend
- **Node.js** & **Express.js** - Server framework
- **MySQL** - Relational database
- **Sequelize** - ORM for database management
- **Firebase** - Authentication services
- **WebSocket** - Real-time communication
- **Nodemailer** - Email notifications
- **Bakong API** - Payment integration
- **JWT** - Token-based authentication
- **Cloudinary** - Image storage and optimization

### Frontend
- **React** with **Vite** - Fast development environment
- **Tailwind CSS** - Utility-first styling
- **Socket.io** - WebSocket client
- **React Toast** - User notifications

### DevOps
- **Docker** & **Docker Compose** - Containerization
- **Nginx** - Reverse proxy and static file serving

---

## Contact

For any inquiries or support, reach out via:
- **Telegram:** [@Reajasey](https://t.me/Reajasey)
- **Facebook:** [Pisey Khenchandara](https://www.facebook.com/pisey.khenchandara)

---

## Acknowledgments

- Bakong API for payment integration
- Cloudinary for image management
- Firebase for authentication services
- All open-source libraries used in this project

---

## License

This project is for showcase purposes. All rights reserved.