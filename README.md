# hindi-dbpedia
```mermaid
flowchart TD
    A[Hindi Wikipedia Article Text] --> B[Hindi Preprocessing (Improved Tokenizer/POS/NER)]
    B --> C[Coreference Resolution (LLM-finetuned or DeepHCoref)]
    C --> D{Relation Extraction (Hybrid)}
    D --> D1[Rule-based OIE (IndIE 2023)]
    D --> D2[Neural OIE (OpenIE6 & mREBEL)]
    D1 & D2 --> E[Combined Triples & Relations]
    E --> F[Entity Linking (mGENRE / ReLiK Retriever-Reader)]
    F --> G[Hallucination Check (SelfCheckGPT & GPT-4 Judge)]
    G --> H{All Facts Verified?}
    H -- "No" --> I[Feedback: Adjust Prompts / Use Different Agent]
    I --> D   %% feedback loop back to relation extraction
    H -- "Yes" --> J[Final Knowledge Graph Output]
```
