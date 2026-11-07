# AI Customer Support

A customer-support chat application with generated replies and conversation storage.

[Open the live demo](https://ai-customer-support-topaz.vercel.app)

![AI Customer Support public homepage](./docs/demo.jpg)

*Public demo homepage, captured November 6, 2026.*

## What it does

- Provides a chat interface for customer questions.
- Streams generated responses from the server.
- Saves conversation messages through Firestore.

## Run locally

You need Node.js, npm, a Google Generative AI API key, and a Firebase project with Firestore configured for your own application.

```bash
git clone https://github.com/gelftheshot/ai-customer-support.git
cd ai-customer-support
npm ci
```

Create `.env.local` in the project root:

```dotenv
GOOGLE_GENERATIVE_AI_API_KEY=your_google_api_key
NEXT_PUBLIC_FIREBASE_API_KEY=your_firebase_web_api_key
```

Update the project-specific Firebase web-app settings in `firebase.js` to match your own Firebase project. Configure Firestore access for that project before using the conversation-storage feature.

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

For a production build:

```bash
npm run build
npm start
```

The existing chat route uses the model configured in `app/api/chat/route.js`. Verify provider access and current model availability when setting up your own environment.

## Main files

- `app/api/chat/route.js`: accepts conversation messages and a chat ID, generates a response stream, and stores the latest user message.
- `app/chat/[chatID]/page.js`: conversation interface.
- `firebase.js`: Firebase/Firestore initialization.

[Project write-up](https://www.lihongebre.com/projects/ai-customer-support)
