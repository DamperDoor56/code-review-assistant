# 🦜️🔗 LangChain + Next.js Starter Template

This template scaffolds a simple LangChain.js + Next.js starter template. It has one endpoint, `POST /api/chat`, that streams a LangChain model call,
then uses Vercel's [AI SDK](https://github.com/vercel-labs/ai) to pipe that stream back to the client and display the incoming messages.

![Screenshot of the title card](/public/images/chat-title-card.png)

## Getting Started

First, you'll need to set up an `.env.local` file. Copy the `.env.local.example` to `.env.local`. To start, you'll just need to add your OpenAI API key.

Next, install the required packages using your preferred package manager (e.g. `yarn`).

Now you're ready to run the development server:

```bash
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result! Ask the bot something and you'll see a streamed response:

![A streaming conversation between the user and the AI](/public/images/chat-conversation.png)

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

Backend logic lives in `app/api/chat/route.ts`. From here, you can change the prompt and model, or add other modules and logic.

## Agents

To try out the conversational agent example, you'll need to give it access to the internet by populating the `SERPAPI_API_KEY` in `.env.local`.
Head over to [the SERP API website](https://serpapi.com/) and get an API key if you don't already have one.

You can then switch to the `Agent` example and try asking it more complex questions:

![A streaming conversation between the user and an AI agent](/public/images/agent-conversation.png)

## Retrieval

The retrieval examples both use Supabase as a vector store. However, you can swap in
[another supported vector store](https://js.langchain.com/docs/modules/data_connection/vectorstores/integrations/) if preferred by changing
the code under `app/api/retrieval/ingest/route.ts`, `app/api/chat/retrieval/route.ts`, and `app/api/chat/retrieval_agents/route.ts`.

For Supabase, follow [these instructions](https://js.langchain.com/docs/modules/data_connection/vectorstores/integrations/supabase) to set up your
database, then get your database URL and private key and paste them into `.env.local`.

You can then switch to the `Retrieval` and `Retrieval Agent` examples. The default document text is pulled from the LangChain.js retrieval
use case docs, but you can change them to whatever text you'd like.

For a given text, you'll only need to press `Upload` once. Pressing it again will re-ingest the docs, resulting in duplicates.

After splitting, embedding, and uploading some text, you're ready to ask questions!

![A streaming conversation between the user and an AI retrieval chain](/public/images/retrieval-chain-conversation.png)

![A streaming conversation between the user and an AI retrieval agent](/public/images/retrieval-agent-conversation.png)

## Learn More

The example chains in the `app/api/chat/route.ts` and `app/api/chat/retrieval/route.ts` files use
[LangChain Expression Language](https://js.langchain.com/docs/guides/expression_language/interface) to
compose different LangChain modules together. You can integrate other retrievers, agents, preconfigured chains, and more too, though keep in mind
`BytesOutputParser` is meant to be used directly with model output.

To learn more about what you can do with LangChain.js, check out the docs here:

- https://js.langchain.com/docs/

## Deploy on Vercel

When ready, you can deploy your app on the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme).

Check out the [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.
