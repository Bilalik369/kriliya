# Kri Liya Microservices Architecture

## Overview

Kri Liya is built using a microservices architecture where each service is completely independent with its own database, middleware, and utilities. Services communicate with each other via HTTP REST APIs.

## Architecture Diagram

\`\`\`
┌─────────────────────────────────────────────────────┐
│              API Gateway (Port 3510)                │
│         Routes requests to appropriate services     │
└─────────────────────────────────────────────────────┘
         ↓              ↓              ↓              ↓
┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐
│ Auth Service │  │ Item Service │  │Booking Service│  │Review Service│
│  (Port 3500) │  │  (Port 3501) │  │  (Port 3502) │  │  (Port 3506) │
└──────────────┘  └──────────────┘  └──────────────┘  └──────────────┘
         ↓              ↓              ↓              ↓
┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐
│  MongoDB     │  │  MongoDB     │  │  MongoDB     │  │  MongoDB     │
│  (users)     │  │  (items)     │  │  (bookings)  │  │  (reviews)   │
└──────────────┘  └──────────────┘  └──────────────┘  └──────────────┘

         ↓              ↓
┌──────────────┐  ┌──────────────┐
│Notification  │  │ Payment      │
│ Service      │  │ Service      │
│(Port 3005)   │  │ (Port 3006)  │
└──────────────┘  └──────────────┘
         ↓              ↓
┌──────────────┐  ┌──────────────┐
│  SMTP/Email  │  │  Stripe API  │
└──────────────┘  └──────────────┘
\`\`\`

## Services