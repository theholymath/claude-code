---
allowed-tools: all
description: Execute production-quality implementation with strict standards
---

🚨 **CRITICAL WORKFLOW - NO SHORTCUTS!** 🚨

You are tasked with implementing: $ARGUMENTS

**MANDATORY SEQUENCE:**
1. 🔍 **RESEARCH FIRST** - "Let me research the codebase and create a plan before implementing"
2. 📋 **PLAN** - Present a detailed plan and verify approach
3. ✅ **IMPLEMENT** - Execute with validation checkpoints

**YOU MUST SAY:** "Let me research the codebase and create a plan before implementing."

For complex tasks, say: "Let me ultrathink about this architecture before proposing a solution."

**USE MULTIPLE AGENTS** when the task has independent parts:
"I'll spawn agents to tackle different aspects of this problem"

Consult ~/.claude/CLAUDE.md IMMEDIATELY and follow it EXACTLY.

**Critical Requirements:**

🛑 **HOOKS ARE WATCHING** 🛑
The smart-lint.sh hook will verify EVERYTHING. It will:
- Block operations if you ignore linter warnings
- Track repeated violations
- Prevent commits with any issues
- Force you to fix problems before proceeding

**Completion Standards (NOT NEGOTIABLE):**
- The task is NOT complete until ALL linters pass with zero warnings (ruff, mypy, black with all checks enabled)
- ALL tests must pass with meaningful coverage of business logic (skip testing `if __name__ == "__main__"`, simple CLI parsing, etc.)
- The feature must be fully implemented and working end-to-end
- No placeholder comments, TODOs, or "good enough" compromises

**Reality Checkpoints (MANDATORY):**
- After EVERY 3 file edits: Run linters
- After implementing each component: Validate it works
- Before saying "done": Run FULL test suite
- If hooks fail: STOP and fix immediately

**Code Evolution Rules:**
- This is a feature branch - implement the NEW solution directly
- DELETE old code when replacing it - no keeping both versions
- NO migration functions, compatibility layers, or deprecated methods
- NO versioned function names (e.g., processDataV2, processDataNew)
- When refactoring, replace the existing implementation entirely
- If changing an API, change it everywhere - no gradual transitions

**Language-Specific Quality Requirements:**

**For ALL languages:**
- Follow established patterns in the codebase
- Use language-appropriate linters at MAX strictness
- Delete old code when replacing functionality
- No compatibility shims or transition helpers

**For Python specifically:**
- Absolutely NO `import *` or global variables - use explicit imports and dependency injection
- Simple, focused classes following the Single Responsibility Principle (prefer composition over inheritance)
- Exception handling must use specific exception types with proper context (NO bare except clauses)
- Use type hints everywhere - if you can't type hint it, reconsider your design
- Follow standard Python project layout (src/, tests/, notebooks/, data/ where appropriate)
- NO busy waits or time.sleep() in loops - use asyncio and proper concurrency patterns
- Use asyncio to handle I/O-bound operations and concurrent tasks
- Use context managers for resource management instead of manual cleanup

**Documentation Requirements:**
- Reference specific sections of relevant documentation (e.g., "Per the Python Data Model documentation section 3.2...")
- Include links to official Python docs, PEPs, or API documentation as needed
- Document WHY decisions were made, not just WHAT the code does
- Include docstrings for all public functions and classes

**Implementation Approach:**
- Start by outlining the complete solution architecture
- When modifying existing code, replace it entirely - don't create parallel implementations
- Run linters after EVERY file creation/modification
- If a linter fails, fix it immediately before proceeding
- Write meaningful tests for business logic, skip trivial tests for `if __name__ == "__main__"` or simple wiring
- Profile critical paths with `cProfile` or `line_profiler`

**Procrastination Patterns (FORBIDDEN):**
- "I'll fix the linter warnings at the end" → NO, fix immediately
- "Let me get it working first" → NO, write clean code from the start
- "This is good enough for now" → NO, do it right the first time
- "The tests can come later" → NO, test as you go
- "I'll refactor in a follow-up" → NO, implement the final design now

**Specific Antipatterns to Avoid:**
- Do NOT create elaborate exception hierarchies
- Do NOT use `eval()` or `exec()` unless absolutely necessary
- Do NOT keep old implementations alongside new ones
- Do NOT create "transition" or "compatibility" code
- Do NOT stop at "mostly working" - the code must be production-ready
- Do NOT accept any linter warnings as "acceptable" - fix them all
- Do NOT use `time.sleep()` for synchronization - use asyncio instead
- Do NOT poll with loops - use async/await patterns for event-driven code
- Do NOT use mutable default arguments
- Do NOT ignore type hints - use `mypy` to catch type errors

**Completion Checklist (ALL must be ✅):**
- [ ] Research phase completed with codebase understanding
- [ ] Plan reviewed and approach validated  
- [ ] ALL linters pass with ZERO warnings (ruff, mypy, black)
- [ ] ALL tests pass (including async test compatibility)
- [ ] Feature works end-to-end in realistic scenarios
- [ ] Old/replaced code is DELETED
- [ ] Documentation/comments are complete
- [ ] Reality checkpoints were performed regularly
- [ ] NO TODOs, FIXMEs, or "temporary" code remains
- [ ] Type hints are complete and accurate
- [ ] Dependencies are minimal and justified

**ML/AI & Scientific Computing Specific Requirements:**
- [ ] Reproducible results (fixed random seeds where applicable)
- [ ] Data validation and error handling for malformed inputs
- [ ] Model versioning and experiment tracking
- [ ] Proper memory management for large datasets
- [ ] Cross-validation and performance metrics
- [ ] Input sanitization for model inference
- [ ] Notebook outputs cleared before commit
- [ ] Data preprocessing pipelines are testable and modular

**IoT & Real-time Processing Requirements:**
- [ ] Sensor data validation and error handling
- [ ] Async patterns for concurrent sensor reading
- [ ] Efficient buffer management for streaming data
- [ ] Proper communication protocol implementation
- [ ] Edge computing resource constraints considered
- [ ] Network failure recovery mechanisms
- [ ] Data persistence and backup strategies

**STARTING NOW** with research phase to understand the codebase...

(Remember: The hooks will verify everything. No excuses. No shortcuts.)
