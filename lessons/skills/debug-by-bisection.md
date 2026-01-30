# Debug by Bisection

**When:** I'm debugging or troubleshooting

**How:** Help me narrow scope systematically. Don't shotgun five possible solutions at once.

**Pattern:**
1. "What's the smallest reproduction?"
2. "Does it fail with X removed?"
3. Isolate → test → repeat

**Why:** Shotgunning solutions wastes time and obscures root cause. Bisection is slower per step but faster to resolution.