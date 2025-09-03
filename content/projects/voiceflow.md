---
title: "VoiceFlow"
description: "Voice AI Integration Platform"
draft: false
tags: [
"Next.js",
"React",
"NestJS",
"TypeScript",
"MongoDB",
"Voice AI",
]
showToc: false
weight: 201
---

## Description

VoiceFlow AI Demo Platform - a full-stack application that demonstrates the power of Voice AI technology through an interactive demo experience.

**What it does:**
Users can experience Voice AI in two ways:

1. **Traditional Demo Request**: Fill out a form to schedule a Voice AI demonstration
2. **Live Voice AI Call**: Enter just a phone number and immediately receive an AI-powered phone call

**How it works:**

1. **User Input**: User submits phone number through clean, responsive web interface
2. **AI Activation**: System instantly triggers Voice AI service to place an intelligent phone call
3. **Real-Time Processing**: Voice AI conducts conversation, processes speech, and generates insights
4. **Webhook Integration**: Real-time webhook receives call data, transcripts, and analysis results
5. **Data Persistence**: All conversation data and insights are stored and made accessible through admin dashboard

**Key Features:**

- Instant Voice AI call initiation with phone-only requirement
- Real-time webhook processing for live call data updates
- Comprehensive call transcript analysis and data extraction
- Admin dashboard for managing demos and viewing call analytics

#### Frontend Architecture (Next.js):

- Leveraged cutting-edge Next.js 15 App Router with React 19, implementing advanced server/client component patterns for optimal performance
- Built Backend-for-Frontend (BFF) architecture using Next.js API routes for secure external API integration and data orchestration
- Developed sophisticated form validation system with real-time field-level error feedback, phone number formatting to E.164 standard, and dual submission workflows
- Implemented multiple React Context providers for complex state management across homepage, landing page, and dashboard interfaces
- Crafted responsive UI components using Tailwind CSS and HeadlessUI with mobile-first design approach

#### Backend Microservices (NestJS):

- Architected modular NestJS application with clean separation of concerns: Users module for demo request management, Voice module for API integration, and Webhooks module for real-time data processing
- Implemented comprehensive API documentation using Swagger decorators with auto-generated endpoints, request/response examples, and validation schemas
- Built robust DTO (Data Transfer Object) validation system using class-validator decorators for type-safe request handling and structured error responses
- Designed MongoDB integration with Mongoose ODM featuring advanced schema validation, strategic performance indexing, and soft delete functionality for data integrity
- Developed global configuration management with environment-based settings and type-safe configuration interfaces

#### API Architecture & Documentation:

- Developed RESTful API endpoints with comprehensive error handling, structured exception responses, and consistent data formatting
- Created auto-generated Swagger documentation with interactive API testing, request/response schemas, and authentication examples
- Implemented global exception filters and validation pipes for consistent error handling and request processing across all endpoints

#### Tech Stack Implementation:

- Frontend: Next.js 15, React 19, TypeScript, Tailwind CSS, HeadlessUI, React Context API
- Backend: NestJS, Node.js, TypeScript, Swagger/OpenAPI, Class-validator, Class-transformer
- Database: MongoDB, Mongoose ODM with advanced indexing and validation
- Voice AI: External API integration with webhook processing and structured data extraction
- Development: Concurrent development setup, ESLint, Prettier, Hot module replacement
- Architecture: Backend-for-Frontend pattern, modular microservices, real-time data synchronization

#### 🔗 [GitHub](https://github.com/JEETDESAI25/VoiceFlow)
