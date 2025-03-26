# User Flow Diagram

```
┌─────────────────┐
│                 │
│   Home Screen   │
│                 │
└────────┬────────┘
         │
         ▼
┌─────────────────┐     ┌─────────────────┐
│                 │     │                 │
│  Registration   │◄────┤     Login       │
│                 │     │                 │
└────────┬────────┘     └────────┬────────┘
         │                       │
         │                       │
         ▼                       ▼
┌─────────────────┐     ┌─────────────────┐
│                 │     │                 │
│  Role Selection │     │ NFT/Wallet Auth │
│                 │     │                 │
└────────┬────────┘     └────────┬────────┘
         │                       │
         └───────────┬───────────┘
                     │
                     ▼
         ┌───────────────────────┐
         │                       │
         │   User Type Router    │
         │                       │
         └───────────┬───────────┘
                     │
         ┌───────────┴───────────┐
         │                       │
┌────────▼─────┐ ┌─────▼──────┐ ┌▼────────────┐ ┌────────▼─────┐ ┌─────▼──────┐
│              │ │            │ │             │ │              │ │            │
│    Client    │ │   Broker   │ │   Supplier  │ │    Trainer   │ │    Admin   │
│  Dashboard   │ │ Dashboard  │ │  Dashboard  │ │  Dashboard   │ │ Dashboard  │
│              │ │            │ │             │ │              │ │            │
└──────┬───────┘ └──────┬─────┘ └──────┬──────┘ └──────┬───────┘ └──────┬─────┘
       │                │             │               │                │
       ▼                ▼             ▼               ▼                ▼
┌──────────────┐ ┌─────────────┐ ┌────────────┐ ┌─────────────┐ ┌─────────────┐
│              │ │             │ │            │ │             │ │             │
│ Find Brokers │ │Find Supplier│ │ My Products│ │ My Trainings│ │  User Mgmt  │
│              │ │             │ │            │ │             │ │             │
└──────────────┘ └─────────────┘ └────────────┘ └─────────────┘ └─────────────┘
       │                │             │               │                │
       ▼                ▼             ▼               ▼                ▼
┌──────────────┐ ┌─────────────┐ ┌────────────┐ ┌─────────────┐ ┌─────────────┐
│              │ │             │ │            │ │             │ │             │
│My Connections│ │ Find Trainer│ │ Add Product│ │Create Course│ │Verifications│
│              │ │             │ │            │ │             │ │             │
└──────────────┘ └─────────────┘ └────────────┘ └─────────────┘ └─────────────┘
       │                │             │               │                │
       ▼                ▼             ▼               ▼                ▼
┌──────────────┐ ┌─────────────┐ ┌────────────┐ ┌─────────────┐ ┌─────────────┐
│              │ │             │ │            │ │             │ │             │
│ Track Orders │ │Active Orders│ │  Orders    │ │  Bookings   │ │  Disputes   │
│              │ │             │ │            │ │             │ │             │
└──────────────┘ └─────────────┘ └────────────┘ └─────────────┘ └─────────────┘
       │                │             │               │                │
       ▼                ▼             ▼               ▼                ▼
┌──────────────┐ ┌─────────────┐ ┌────────────┐ ┌─────────────┐ ┌─────────────┐
│              │ │             │ │            │ │             │ │             │
│   Messages   │ │  Messages   │ │  Messages  │ │  Messages   │ │ System Logs │
│              │ │             │ │            │ │             │ │             │
└──────────────┘ └─────────────┘ └────────────┘ └─────────────┘ └─────────────┘
       │                │             │               │                │
       └────────┬───────┴─────────────┼───────────────┴────────────────┘
                │                     │
                ▼                     ▼
        ┌───────────────┐    ┌────────────────┐
        │               │    │                │
        │ Chat System   │    │ Payment System │
        │               │    │                │
        └───────────────┘    └────────────────┘
                │                     │
                └─────────┬───────────┘
                          │
                          ▼
                  ┌───────────────┐
                  │               │
                  │  Blockchain   │
                  │  Traceability │
                  │               │
                  └───────────────┘
```

## Key User Flows

### 1. New User Registration Flow
- Home Screen → Registration → Role Selection → User Type Dashboard

### 2. Returning User Login Flow
- Home Screen → Login → User Type Dashboard

### 3. NFT/Wallet Authentication Flow
- Home Screen → NFT/Wallet Auth → User Type Dashboard

### 4. Client-Broker Connection Flow
- Client Dashboard → Find Brokers → View Broker Profile → Send Connection Request
- Broker Dashboard → Client Requests → Accept/Decline Request

### 5. Broker-Supplier Connection Flow
- Broker Dashboard → Find Supplier → View Supplier Profile → Send Connection Request
- Supplier Dashboard → Connection Requests → Accept/Decline Request

### 6. Order Processing Flow
- Client Dashboard → Find Broker → Place Order
- Broker Dashboard → Active Orders → Process Order
- Broker Dashboard → Find Supplier → Forward Order
- Supplier Dashboard → Orders → Process Order
- Blockchain Traceability → Record Product Journey

### 7. Payment Processing Flow
- Client Dashboard → Track Orders → Make Payment
- Payment System → Process Transaction
- Broker Dashboard → Active Orders → Confirm Payment
- Supplier Dashboard → Orders → Receive Payment

### 8. Communication Flow
- Any Dashboard → Messages → Chat System → Send/Receive Messages

### 9. Dispute Resolution Flow
- Any Dashboard → Report Issue
- Admin Dashboard → Disputes → Review → Mediate

### 10. Training Booking Flow
- Broker Dashboard → Find Trainer → View Trainer Profile → Request Training
- Trainer Dashboard → Training Requests → Accept/Propose Time
- Broker Dashboard → Messages → Confirm Training

## Transition Patterns

### Modal Transitions
- Quick actions that don't require full screen navigation
- Examples: Confirmation dialogs, quick filters, small forms

### Push Transitions
- Standard screen-to-screen navigation
- Maintains navigation history for back button functionality

### Tab Transitions
- Switching between main sections within a dashboard
- Preserves state within each tab

### Drawer Transitions
- Side menu navigation to main app sections
- Accessible from any screen via the hamburger menu icon

## Accessibility Considerations

- All flows should be navigable via keyboard/screen reader
- Critical paths should have minimal steps (3-5 max)
- Error states and recovery paths are clearly defined
- Alternative flows provided for complex interactions
