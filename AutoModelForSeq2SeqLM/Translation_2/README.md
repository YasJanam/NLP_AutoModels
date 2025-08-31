```mermaid
flowchart LR
    subgraph EncoderStack [Encoder Stack]
        E1[Encoder 1]
        E2[Encoder 2]
        E3[Encoder 3]
        E1 --> E2 --> E3
    end

    subgraph DecoderStack [Decoder Stack]
        D1[Decoder 1]
        D2[Decoder 2]
        D3[Decoder 3]
        D1 --> D2 --> D3
    end

    E1 -. Cross-Attention .-> D1
    E2 -. Cross-Attention .-> D2
    E3 -. Cross-Attention .-> D3

