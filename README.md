# SYNAPSE
A systems design proposal for a dual-cache, quantum-inspired memory architecture for AI agents.
<img width="1448" height="1086" alt="image" src="https://github.com/user-attachments/assets/e075c1be-a26b-4f69-bb26-62c8d99218f0" />


# Architecture

The SYNAPSE architecture utilizes dual-cache mechanism for hot, live, application
instance as the AI agent continuously interact with the user. This ensures that strong
short-term memory is enforced, along with complexity provided by the hilbert space and optimized 
through Numba JIT. It balances the native normal caching mechanism for hardware compliance and the 
quantum association for comlexity.

A middleware is also used that acts as the "transport" layer for the agent's brain
passing down the memories all the way to the Neo4j Graph DB for human-like long-term memory.

The overall concept for hilbert space caching lies on the mathematics of hilbert space, specifically, its
ability to scale its dimension. For SYNEURO, having interactions with the AI agent e.g Text Conversation
would be considered as a *temporal* activity modelled as a continuous function each interaction. For every 
interaction, there is a chance of the AI to ignore irrelevant information which causes the continuous
function to collapse. This not only maintains welfare of the memory but also mimics real-life human attention
spans.

Furthermore, as the user and AI interacts on prolonged hours,  the *temporal* activites generated may be 
consolidated and strengthened further, acting as the basis for future long-term memory formulation. The half hibert
cache also serves as persistency for stateful interactions with the AI, ensuring that it does not easily forget 
what has been said after a long period of time. 

To demonstrate, the AI would be able to remember what has been interacted with previously if the user 
were to bring it up, as their interactions generates *temporal* activities which then becomes a 
continuous function inside the cache, and scaling up as there is new activity.

```text

========================================================================================
                                     THE USER PAYLOAD
                           "I feel completely overwhelmed right now."
========================================================================================
                                             │
                       ┌─────────────────────┴─────────────────────┐
                       ▼                                           ▼
         [ CHRONOLOGICAL TIMELINE ]                     [ STATE TRAJECTORY MATRIX ]
         synapse_normal_chat_cache                     synapse_hilbert_cache
 ┌───────────────────────────────────────┐   ┌───────────────────────────────────────┐
 │ TIME       │ ROLE  │ MESSAGE          │   │ VECTOR ID  │ COMPLEX COORDINATE (Cⁿ)  │
 ├────────────┼───────┼──────────────────┤   ├────────────┼──────────────────────────┤
 │ 20:00:00   │ User  │ Stressed...      │◀──┼─▶ 55432189 │ [1.0+2.0j,  3.0-4.0j]    │
 │ 20:15:30   │ User  │ Manager...       │◀──┼─▶ 88214753 │ [1.5+2.5j,  2.0-5.5j]    │
 │ 21:00:00   │ User  │ Overwhelmed...   │◀──┼─▶ 12948576 │ [4.0+6.0j, -1.0-8.0j]    │
 └───────────────────────────────────────┘   └───────────────────────────────────────┘
                                                           │
                                                           ▼
                                               [ QUANTUM-INSPIRED ENGINE ]
                                               HilbertSpace Operators (Numba)
                                             ┌───────────────────────────────────┐
                                             │ • Calculates Wave Interference    │
                                             │ • Applies Phase Rotation Matrices │
                                             │ • Triggers Superposition Collapse │
                                             └───────────────────────────────────┘
                                                           │
                                                           ▼
========================================================================================
                                   MEMORY RETRIEVAL FILTER
========================================================================================
   1. The engine checks the current math state against historical Hilbert vectors.
   2. Vector 12948576 (Panic) and Vector 55432189 (Stress) constructively interfere.
   3. The Linker extracts those specific IDs, ignoring irrelevant intermediate chats.
   4. The system hydates the IDs with raw text, sending deep structural context to the LLM.
========================================================================================
```
