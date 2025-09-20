# Lead Management System - Frontend

A modern React.js frontend application for the Lead Management System built for Erino SDE Internship Assignment.

## 🚀 Features

- **Modern UI**: Built with React 18 and Tailwind CSS
- **Interactive Authentication**: Beautiful login/register pages with animations
- **Lead Management**: Full CRUD operations with intuitive forms
- **Data Grid**: AG Grid for efficient data display with server-side pagination
- **Advanced Filtering**: Real-time filtering with multiple operators
- **Responsive Design**: Mobile-first approach with modern glassmorphism effects
- **Form Validation**: React Hook Form with comprehensive validation
- **Toast Notifications**: User feedback with React Hot Toast

## 🛠️ Tech Stack

- **Framework**: React 18.2.0
- **Build Tool**: Vite
- **Styling**: Tailwind CSS
- **Routing**: React Router DOM
- **Data Grid**: AG Grid React
- **Forms**: React Hook Form
- **HTTP Client**: Axios
- **Notifications**: React Hot Toast
- **Icons**: Heroicons (SVG)

## 📋 Prerequisites

- Node.js (v14 or higher)
- npm or yarn
- Backend API running on port 5000

## 🔧 Installation

1. **Clone the repository**

   ```bash
   git clone <repository-url>
   cd lead-management-system/frontend
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

3. **Start the development server**

   ```bash
   npm run dev
   ```

4. **Open your browser**
   Navigate to `http://localhost:3000`

## 🎨 UI Components

### Authentication Pages

- **Login Page**: Interactive form with password visibility toggle
- **Register Page**: Multi-step registration with validation
- **Glassmorphism Design**: Modern frosted glass effects
- **Gradient Backgrounds**: Beautiful color transitions
- **Loading States**: Smooth loading animations

### Dashboard

- **Statistics Cards**: Key metrics display
- **Advanced Filters**: Real-time filtering with multiple operators
- **Data Grid**: AG Grid with server-side pagination
- **Action Buttons**: Edit/Delete with confirmation dialogs
- **Status Badges**: Color-coded status and source indicators

### Lead Form

- **Organized Sections**: Personal, Contact, Company, and Lead Details
- **Form Validation**: Real-time validation with error messages
- **Auto-save**: Form state preservation
- **Responsive Layout**: Mobile-friendly design

## 📱 Responsive Design

The application is fully responsive with breakpoints:

- **Mobile**: < 640px
- **Tablet**: 640px - 1024px
- **Desktop**: > 1024px

## 🎯 Key Features

### Authentication Flow

```javascript
// Login with test credentials
Email: test@example.com
Password: testpassword123
```

### Lead Management

- **Create**: Add new leads with comprehensive form
- **Read**: View leads in paginated grid
- **Update**: Edit existing leads
- **Delete**: Remove leads with confirmation

### Advanced Filtering

- **Status Filter**: new, contacted, qualified, lost, won
- **Source Filter**: website, facebook_ads, google_ads, referral, events, other
- **Score Range**: Filter by lead score (0-100)
- **Value Range**: Filter by lead value
- **Date Filters**: Created date, last activity date
- **Qualification**: Filter by qualified/unqualified leads

## 🔌 API Integration

### Authentication Context

```javascript
// AuthContext provides:
const { user, login, register, logout, loading } = useAuth();
```

### Lead Operations

```javascript
// Create lead
await axios.post("/api/leads", leadData);

// Get leads with pagination
await axios.get("/api/leads?page=1&limit=20");

// Update lead
await axios.put(`/api/leads/${id}`, updateData);

// Delete lead
await axios.delete(`/api/leads/${id}`);
```

## 🎨 Styling System

### Tailwind CSS Configuration

```javascript
// tailwind.config.js
module.exports = {
  content: ["./src/**/*.{js,jsx,ts,tsx}"],
  theme: {
    extend: {
      animation: {
        "fade-in": "fadeIn 0.5s ease-in-out",
        "slide-up": "slideUp 0.3s ease-out",
      },
    },
  },
};
```

### Component Styling

- **Utility Classes**: Tailwind CSS utility classes
- **Custom Animations**: Fade-in, slide-up effects
- **Color System**: Consistent color palette
- **Typography**: Modern font stack

## 📊 Data Grid Configuration

### AG Grid Setup

```javascript
const columnDefs = [
  { headerName: "Name", field: "first_name", width: 150 },
  { headerName: "Email", field: "email", width: 200 },
  { headerName: "Company", field: "company", width: 180 },
  {
    headerName: "Status",
    field: "status",
    width: 120,
    cellRenderer: StatusCell,
  },
  {
    headerName: "Source",
    field: "source",
    width: 120,
    cellRenderer: SourceCell,
  },
  { headerName: "Score", field: "score", width: 100 },
  { headerName: "Value", field: "lead_value", width: 120 },
  {
    headerName: "Actions",
    field: "actions",
    width: 150,
    cellRenderer: ActionsCell,
  },
];
```

### Server-side Pagination

```javascript
const onGridReady = (params) => {
  setGridApi(params.api);
  setColumnApi(params.columnApi);
  fetchLeads();
};

const fetchLeads = async (page = 1, limit = 20) => {
  const response = await axios.get(`/api/leads?page=${page}&limit=${limit}`);
  setLeads(response.data.data);
  setPagination(response.data);
};
```

## 🧪 Testing

### Manual Testing

1. **Authentication**: Test login/register flows
2. **Lead CRUD**: Create, read, update, delete leads
3. **Filtering**: Test all filter combinations
4. **Pagination**: Navigate through pages
5. **Responsive**: Test on different screen sizes

### Test Credentials

```
Email: test@example.com
Password: testpassword123
```

## 🚀 Build and Deployment

### Development

```bash
npm run dev
```

### Production Build

```bash
npm run build
```

### Preview Production Build

```bash
npm run preview
```

### Deployment (Vercel)

```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel --prod
```

## 📁 Project Structure

```
frontend/
├── public/
│   └── vite.svg
├── src/
│   ├── components/
│   │   ├── Layout.jsx          # Main layout component
│   │   └── ProtectedRoute.jsx   # Route protection
│   ├── contexts/
│   │   └── AuthContext.jsx     # Authentication context
│   ├── pages/
│   │   ├── Login.jsx           # Login page
│   │   ├── Register.jsx        # Register page
│   │   ├── Dashboard.jsx       # Dashboard with leads grid
│   │   └── LeadForm.jsx        # Lead create/edit form
│   ├── App.jsx                 # Main app component
│   ├── main.jsx                # App entry point
│   └── index.css               # Global styles
├── package.json                # Dependencies and scripts
├── vite.config.js             # Vite configuration
├── tailwind.config.js          # Tailwind CSS configuration
└── README.md                   # This file
```

## 🎨 Design System

### Color Palette

- **Primary**: Blue (#3B82F6)
- **Secondary**: Indigo (#6366F1)
- **Success**: Green (#10B981)
- **Warning**: Yellow (#F59E0B)
- **Error**: Red (#EF4444)
- **Neutral**: Gray (#6B7280)

### Typography

- **Font Family**: Inter, system-ui, sans-serif
- **Headings**: Font weight 600-700
- **Body**: Font weight 400-500
- **Small Text**: Font weight 400

### Spacing

- **Base Unit**: 4px
- **Common Spacing**: 4, 8, 12, 16, 20, 24, 32, 40, 48, 64px

## 🔧 Configuration

### Vite Configuration

```javascript
// vite.config.js
export default defineConfig({
  plugins: [react(), tailwindcss()],
  server: {
    port: 3000,
    proxy: {
      "/api": {
        target: "http://localhost:5000",
        changeOrigin: true,
        secure: false,
      },
    },
  },
});
```

### Environment Variables

```env
VITE_API_URL=http://localhost:5000
VITE_APP_NAME=Lead Management System
```

## 🐛 Troubleshooting

### Common Issues

1. **CORS Errors**: Ensure backend CORS is configured for frontend URL
2. **Proxy Issues**: Check Vite proxy configuration
3. **Build Errors**: Clear node_modules and reinstall dependencies
4. **Styling Issues**: Ensure Tailwind CSS is properly configured

### Debug Commands

```bash
# Clear cache
npm run clean

# Reinstall dependencies
rm -rf node_modules package-lock.json
npm install

# Check for updates
npm outdated
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License.

## 🆘 Support

For support or questions, please contact the development team or create an issue in the repository.

## 🎯 Future Enhancements

- [ ] Dark mode toggle
- [ ] Advanced search functionality
- [ ] Lead import/export features
- [ ] Real-time notifications
- [ ] Advanced analytics dashboard
- [ ] Mobile app (React Native)
- [ ] Offline support (PWA)
