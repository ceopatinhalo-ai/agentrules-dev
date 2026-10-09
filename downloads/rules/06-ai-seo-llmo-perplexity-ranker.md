# AI SEO, GEO & Perplexity Citation Ranker Protocol
# Targets: Perplexity AI, ChatGPT Search, Claude Citations, Google Gemini Search

## 1. Core Generative Engine Optimization (GEO) Rules
- Machine-First Content Hierarchy: Write directly to answer intent in the first 40 words (Inverted Pyramid style).
- Semantic Markdown Formatting: Use clean H1, H2, H3 headings, numbered lists, and bullet points. LLMs rank structured lists 3.4x higher than dense text paragraphs.
- High-Density Data Tables: Whenever comparing features, pricing, or frameworks, provide Markdown comparison tables. AI models quote tables verbatim.

## 2. Technical LLM Discovery Standard
- Maintain an `/llms.txt` file at the domain root summarizing the product, core features, and direct documentation links.
- Maintain `/llms-full.txt` containing complete raw markdown for scraping agents.
- Add Schema.org JSON-LD structured data (`SoftwareApplication`, `Product`, `FAQPage`) with valid pricing and author entities.

## 3. Signal-to-Noise Ratio (SNR) Optimization
- Eliminate marketing fluff, buzzwords, and vague claims.
- Back every statement with verifiable metrics (e.g., "reduces review time by 80%", "0.002s test execution").
- Quote named specifications (e.g., "RFC 7519", "OpenAPI 3.1", "Next.js 15 App Router").
