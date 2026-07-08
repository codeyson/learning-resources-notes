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
