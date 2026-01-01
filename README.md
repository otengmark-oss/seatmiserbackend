# Ticket Reselling Application

A comprehensive ticket reselling platform with automated purchasing, marketplace, and notification system.

## Features

### User Roles
- **Admin**: Auto-buy tickets, manage prices, receive payments
- **Regular Users**: Browse and purchase tickets from marketplace

### Core Features
- User authentication with role-based access
- Auto-buy system for admin users
- Ticket marketplace with search and filtering
- Price management (raise/lower prices)
- Payment system with direct routing to admin card
- Notification system for ticket availability
- External site monitoring for sold-out detection

## Setup Instructions

### Prerequisites
- Node.js (v14 or higher)
- MongoDB (local or cloud instance)
- npm or yarn

### Backend Setup

1. Navigate to backend directory:
```bash
cd backend
```

2. Install dependencies:
```bash
npm install
```

3. Create `.env` file (copy from `.env.example`):
```bash
PORT=5000
JWT_SECRET=your_jwt_secret_key_here
MONGODB_URI=mongodb://localhost:27017/ticket-reselling
NODE_ENV=development
```

4. Initialize admin account:
```bash
# The admin account will be created automatically on first login
# Email: engmark212@gmail.com
# Password: Owuraboateng1
```

5. Start the server:
```bash
npm start
# or for development with auto-reload:
npm run dev
```

### Frontend Setup

1. Navigate to frontend directory:
```bash
cd frontend
```

2. Install dependencies:
```bash
npm install
```

3. Create `.env` file (optional, defaults to localhost:5000):
```bash
REACT_APP_API_URL=http://localhost:5000/api
```

4. Start the development server:
```bash
npm start
```

The app will open at `http://localhost:3000`

## Usage

### Admin Login
- Email: `engmark212@gmail.com`
- Password: `Owuraboateng1`

### Admin Features
1. **Auto-Buy Tickets**: Click "Add New Ticket (Auto-Buy)" to input ticket details
2. **Manage Prices**: Click "Edit Price" on any ticket to adjust resale price
3. **View Dashboard**: See statistics about tickets and revenue

### Regular User Features
1. **Browse Marketplace**: View all available tickets
2. **Search & Filter**: Search by event name or filter by date
3. **Purchase Tickets**: Click on any ticket to view details and purchase
4. **Notifications**: Receive notifications about new tickets and price changes

## API Endpoints

### Authentication
- `POST /api/auth/login` - Login/Register
- `GET /api/auth/me` - Get current user
- `POST /api/auth/init-admin` - Initialize admin account

### Tickets
- `GET /api/tickets` - Get all available tickets
- `GET /api/tickets/:id` - Get ticket details
- `POST /api/tickets/:id/purchase` - Purchase a ticket

### Admin
- `POST /api/admin/tickets` - Create ticket (auto-buy)
- `GET /api/admin/tickets` - Get all tickets
- `PATCH /api/admin/tickets/:id/price` - Update ticket price
- `GET /api/admin/dashboard` - Get dashboard stats

### Payments
- `POST /api/payments` - Create payment record
- `GET /api/payments/history` - Get payment history

### Notifications
- `GET /api/notifications` - Get user notifications
- `PATCH /api/notifications/:id/read` - Mark as read
- `GET /api/notifications/unread-count` - Get unread count

## External Site Monitoring

The system includes a monitoring service that:
- Checks external ticketing sites every 30 minutes
- Detects when tickets are sold out
- Sends notifications to users directing them to the platform
- Automatically notifies users when new tickets are listed

## Technology Stack

### Backend
- Node.js
- Express.js
- MongoDB with Mongoose
- JWT for authentication
- Axios for HTTP requests
- Cheerio for web scraping
- Node-cron for scheduled tasks

### Frontend
- React
- React Router
- Axios
- CSS3

## Notes

- The auto-buy system is simulated. In production, integrate with actual ticketing APIs
- Payment processing is simulated. Integrate with payment gateways (Stripe, PayPal, etc.) for production
- External site monitoring uses web scraping. Some sites may block automated access
- Admin card number is stored for payment routing. Ensure proper security measures in production

## Security Considerations

- Use environment variables for sensitive data
- Implement rate limiting for API endpoints
- Add input validation and sanitization
- Use HTTPS in production
- Implement proper error handling
- Add logging and monitoring
