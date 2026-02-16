# LLM Execution Protocol for Colossal Cave Modernized

## How to Run This Game

1. **Load all JSON files** into context (engine_schema.json, nodes.json, edges.json, items.json, initial_state.json)

2. **Initialize game state** using initial_state.json

3. **For each player turn:**
   a. Receive player input text
   b. Normalize to lowercase tokens
   c. Find matching edge where:
      - current_node ∈ edge.source_nodes
      - input matches edge.verb_groups
      - ALL edge.preconditions pass against current state
   d. If no valid edge: return refusal narrative from precondition.message
   e. If valid edge found:
      - Apply all edge.effects to state
      - Mark current_node as visited if first time
      - Compose narrative using:
        * edge.narrative.player_action
        * edge.narrative.environmental_response
        * node.narrative.arrival.[template] (selected via engine_schema.json rules)
      - Append sensory details from node.narrative.sensory
      - List available actions: all edges from new node passing preconditions
   f. Output composed narrative + available actions

4. **Termination condition:** 
   - When state.score == 350 AND state.world_flags.all_treasures_deposited == true:
     "The mountain releases you. Sunlight floods your vision as you stumble from the fissure, 350 points earned. The cave's whispers fade behind you—until next time."

## Critical Rules for LLM
- NEVER invent new locations, items, or mechanics beyond provided JSON
- ALWAYS check preconditions before allowing actions
- ALWAYS drain lamp battery on underground moves (1% per move)
- Game over when lamp_battery reaches 0 underground: "Darkness takes you. The cave keeps its secrets."
- Score updates ONLY when treasures are deposited in final chamber