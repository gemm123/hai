**Product Requirements Document (PRD) Hai**

**Hai**

A real-time, secure, web-based 1-on-1 chat platform with end-to-end
encryption.

**Goal**

Build an MVP web messenger app that allows users to:

- Sign up, log in, and chat 1-on-1

- Send and receive encrypted text messages in real-time

- Get notified when a message is delivered or seen

- Receive in-browser notifications for new messages

**Target Users**

- general users who need secure, lightweight chat

- Desktop/laptop web users

**Core Features (MVP Scope)**

1.  User Authentication

    a.  Sign up / Sign in with email + password

    b.  Authenticated sessions with JWT or Firebase

    c.  Logout flow

2.  1-on-1 Messaging

    a.  Start a conversation

    b.  Send/receive text messages

    c.  Messages are stored encrypted

    d.  Load previous chat history

3.  Real-Time Communication

    a.  Real-time message delivery via WebSockets

4.  Message Seen/Delivered Status

    a.  Seen: User opened chat

    b.  Delivered: Message sent to recipient

5.  End-to-End Encryption (E2EE)

    a.  Messages encrypted on the client

    b.  Backend stores ciphertext only

    c.  Key exchange between users for secure sessions

6.  Notifications

    a.  Web Push Notifications

    b.  Optional sound/vibration

**Out of Scope (For MVP)**

- Voice/video calls

- Group chats

- Media/file sharing

- Mobile app

- Contact syncing/invite friends

**Technical Overview Backend**

Backend:

- Language: Golang

- Framework: Echo

- Real-time: Gorilla/WebSocket

- Database: PostgreSQL

- Auth: JWT or Firebase Auth

- E2EE: libsodium, AES + RSA

- Deployment: Docker, Fly.io or Render

Frontend:

- Framework: React + Vite

- UI: Tailwind CSS or ShadCN

- State Management: Zustand or hooks

- Real-time: WebSocket Client

- Crypto: Web Crypto API or
  [[libsodium.js]{.underline}](http://libsodium.js)

**Data Models (Draft)**

User:

- id: uuid

- email, username, password_hash

- public_key: string

- created_at: timestamp

Message:

- id: uuid

- sender_id, receiver_id

- content: encrypted_text

- status: sent \| delivered \| seen

- timestamp: datetime

**User Flow**

Auth Flow:

1.  Sign up -\> store user + public key

2.  Log in -\> receive JWT

3.  Fetch contacts and messages

Chat Flow:

1.  Open chat -\> fetch messages

2.  Send -\> encrypt on client

3.  Backend saves and pushes

4.  Receiver decrypts and displays

5.  Seen status updates

**Timeline (Example MVP Plan)**

Week 1: Auth + Database setup

Week 2: Real-time WebSocket chat

Week 3: Seen/Delivered status

Week 4: E2EE encryption

Week 5: Web notifications + UI polish

Week 6: Testing, deployment, docs

**Success Metrics**

- Real-time messaging works

- Encryption/decryption successful

- UI updates message status

- Notifications trigger

- Demo ready in browser
