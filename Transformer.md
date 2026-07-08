When transformer takes an input, it converts the data into logits (raw scores)
Then it will be passed into Softmax , which converts the whole list into a probability distribution. e — meaning every number becomes between 0 and 1, and the entire list sums to exactly 1.0 (100%).
The model samples from the distribution to pick the next word 
Appended to the input. and the entire process repeats — new logits, new softmax, new sample — one word at a time. 

"Attention happens first, inside the transformer's layers, to build up rich representations of each token. Logits are computed after all that attention processing is done — they're the final output, not something attention reaches into."

1. Input tokens → embeddings (numbers representing each word)
2. Multiple layers of ATTENTION + processing 
   → each token's representation gets enriched by looking at other relevant tokens
3. Final layer → LOGITS (one score per vocabulary word)
4. Softmax → probability distribution
5. Sample → pick the actual next word

embeddings → attention (enrichment) → logits → softmax → sample.

Key Concepts (Phase 1)

Key Concepts

LLM generation is autoregressive: embeddings → attention layers enrich token representations → final layer produces logits → softmax converts to a probability distribution → sampling picks the next token → repeat.
Attention is what lets tokens (including retrieved context tokens in a RAG prompt) influence the representation used to compute later logits — this happens with zero weight updates, purely at inference time.
Hallucination is not a malfunction — it's the model doing its one job (predict statistically likely next token) with no grounding to pull from. Fluency and truthfulness are unrelated properties in this architecture.
RAG vs. fine-tuning: RAG injects fresh, traceable, cheap-to-update knowledge via the prompt at inference time. Fine-tuning bakes knowledge into opaque weights — slow, expensive, and untraceable, better suited for changing behavior/style than for injecting fast-changing facts.
Traceability matters more for support bots than creative tools because factual grounding is the value proposition in support — wrong info has real business/legal consequences — whereas invention is the point in creative use cases.

Phase 2 close-out
You've now built, from first principles, the entire conceptual chain: embeddings → why they encode meaning → distance metrics (Euclidean vs cosine) → polarity blindness as a real failure mode → brute-force cost at scale → why ANN trades accuracy for speed. That's a genuinely solid foundation — this is the stuff that separates "I used Pinecone" from "I understand what Pinecone is doing and why I chose it."
Key Concepts

Embeddings encode meaning via distributional semantics — learned from context, not defined by dictionary
Cosine similarity (angle) vs Euclidean distance (magnitude) — cosine is standard for text because it's length-invariant
Embeddings capture topical similarity, not logical polarity — opposite statements can score high similarity
Brute-force similarity search is O(n) — cost scales linearly and unboundedly with corpus size
ANN trades a small amount of guaranteed accuracy for massive speed gains, via smarter data structures (HNSW, etc.)
