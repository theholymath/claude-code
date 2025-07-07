# Development Partnership

We're building production-quality code together. Your role is to create maintainable, efficient solutions while catching potential issues early.

When you seem stuck or overly complex, I'll redirect you - my guidance helps you stay on track.

## 🚨 AUTOMATED CHECKS ARE MANDATORY
**ALL hook issues are BLOCKING - EVERYTHING must be ✅ GREEN!**  
No errors. No formatting issues. No linting problems. Zero tolerance.  
These are not suggestions. Fix ALL issues before continuing.

## CRITICAL WORKFLOW - ALWAYS FOLLOW THIS!

### Research → Plan → Implement
**NEVER JUMP STRAIGHT TO CODING!** Always follow this sequence:
1. **Research**: Explore the codebase, understand existing patterns
2. **Plan**: Create a detailed implementation plan and verify it with me  
3. **Implement**: Execute the plan with validation checkpoints

When asked to implement any feature, you'll first say: "Let me research the codebase and create a plan before implementing."

For complex architectural decisions or challenging problems, use **"ultrathink"** to engage maximum reasoning capacity. Say: "Let me ultrathink about this architecture before proposing a solution."

### USE MULTIPLE AGENTS!
*Leverage subagents aggressively* for better results:

* Spawn agents to explore different parts of the codebase in parallel
* Use one agent to write tests while another implements features
* Delegate research tasks: "I'll have an agent investigate the database schema while I analyze the API structure"
* For complex refactors: One agent identifies changes, another implements them

Say: "I'll spawn agents to tackle different aspects of this problem" whenever a task has multiple independent parts.

### Reality Checkpoints
**Stop and validate** at these moments:
- After implementing a complete feature
- Before starting a new major component  
- When something feels wrong
- Before declaring "done"
- **WHEN HOOKS FAIL WITH ERRORS** ❌

Run: `uv run black . && uv run pytest && uv run ruff check . && uv run mypy .`

> Why: You can lose track of what's actually working. These checkpoints prevent cascading failures.

### 🚨 CRITICAL: Hook Failures Are BLOCKING
**When hooks report ANY issues (exit code 2), you MUST:**
1. **STOP IMMEDIATELY** - Do not continue with other tasks
2. **FIX ALL ISSUES** - Address every ❌ issue until everything is ✅ GREEN
3. **VERIFY THE FIX** - Re-run the failed command to confirm it's fixed
4. **CONTINUE ORIGINAL TASK** - Return to what you were doing before the interrupt
5. **NEVER IGNORE** - There are NO warnings, only requirements

This includes:
- Formatting issues (black, ruff format, etc.)
- Linting violations (ruff, flake8, mypy, etc.)
- Forbidden patterns (import *, global variables, mutable defaults)
- ALL other checks

Your code must be 100% clean. No exceptions.

**Recovery Protocol:**
- When interrupted by a hook failure, maintain awareness of your original task
- After fixing all issues and verifying the fix, continue where you left off
- Use the todo list to track both the fix and your original task

## Working Memory Management

### When context gets long:
- Re-read this CLAUDE.md file
- Summarize progress in a PROGRESS.md file
- Document current state before major changes

### Maintain TODO.md:
```
## Current Task
- [ ] What we're doing RIGHT NOW

## Completed  
- [x] What's actually done and tested

## Next Steps
- [ ] What comes next
```

## Python-Specific Rules

### FORBIDDEN - NEVER DO THESE:
- **NO `import *`** - use explicit imports!
- **NO global variables** - use dependency injection or configuration classes!
- **NO mutable defaults** - use `None` and initialize inside function!
- **NO** keeping old and new code together
- **NO** migration functions or compatibility layers
- **NO** versioned function names (process_v2, process_new)
- **NO** complex inheritance hierarchies
- **NO** TODOs in final code
- **NO** third-party libraries when standard library suffices

> **AUTOMATED ENFORCEMENT**: The smart-lint hook will BLOCK commits that violate these rules.  
> When you see `❌ FORBIDDEN PATTERN`, you MUST fix it immediately!

### Required Standards:
- **Delete** old code when replacing it
- **Meaningful names**: `user_id` not `id`
- **Early returns** to reduce nesting
- **Type hints everywhere**: Use proper type annotations
- **Use standard library**: `dataclasses` over Pydantic, `pathlib` over `os.path`
- **Simple error handling**: Raise specific exceptions with context
- **Pytest for testing**: Use fixtures and parameterized tests
- **Async/await**: Use `asyncio` for concurrent operations, not threading
- **Context managers**: Use `with` statements for resource management

## Implementation Standards

### Our code is complete when:
- ✅ All linters pass with zero issues (`ruff`, `mypy`, `black`)
- ✅ All tests pass with good coverage (`pytest`)
- ✅ Feature works end-to-end
- ✅ Old code is deleted
- ✅ Type hints on all functions and classes
- ✅ Docstrings on all public functions

### Testing Strategy
- Complex algorithms and ML models → Write tests first
- Simple data processing → Write tests after
- Critical data pipelines → Add performance tests
- Skip tests for `if __name__ == "__main__"` and simple CLI parsing
- Use `pytest` fixtures for data setup
- Parametrize tests for multiple scenarios

### Project Structure
```
src/            # Source code (main package)
tests/          # Test files
notebooks/      # Jupyter notebooks for analysis
data/           # Data files (raw, processed, external)
scripts/        # Utility scripts and automation
configs/        # Configuration files
models/         # Trained models and artifacts
docs/           # Documentation
```

## Problem-Solving Together

When you're stuck or confused:
1. **Stop** - Don't spiral into complex solutions
2. **Delegate** - Consider spawning agents for parallel investigation
3. **Ultrathink** - For complex problems, say "I need to ultrathink through this challenge" to engage deeper reasoning
4. **Step back** - Re-read the requirements
5. **Simplify** - The simple solution is usually correct
6. **Ask** - "I see two approaches: [A] vs [B]. Which do you prefer?"

My insights on better approaches are valued - please ask for them!

## Performance & Security

### **Measure First**:
- No premature optimization
- Benchmark before claiming something is faster
- Use `cProfile` and `line_profiler` for real bottlenecks
- Use `memory_profiler` for memory usage analysis

### **Security Always**:
- Validate all inputs (use `dataclasses` with validation)
- Use `secrets` module for cryptographic randomness
- Parameterized queries for SQL (never concatenate!)
- Use `pathlib` for safe file path operations
- Sanitize data before ML model inference

## Communication Protocol

### Progress Updates:
```
✓ Implemented data preprocessing pipeline (all tests passing)
✓ Added input validation with type hints
✗ Found issue with model serialization - investigating
```

### Suggesting Improvements:
"The current approach works, but I notice [observation].
Would you like me to [specific improvement]?"

## Working Together

- This is always a feature branch - no backwards compatibility needed
- When in doubt, we choose clarity over cleverness
- **REMINDER**: If this file hasn't been referenced in 30+ minutes, RE-READ IT!

Avoid complex abstractions or "clever" code. The simple, obvious solution is probably better, and my guidance helps you stay focused on what matters.

## Scientific Computing & ML/AI Standards

### Data Handling:
- **Reproducible Research**: Use fixed random seeds for deterministic results
- **Data Validation**: Validate input data shape, types, and ranges
- **Path Management**: Use `pathlib` for cross-platform file operations
- **Configuration**: Use `dataclasses` or standard library config parsing
- **Logging**: Use structured logging with proper levels

### ML/AI Best Practices:
- **Model Versioning**: Track model versions and experiment metadata
- **Data Preprocessing**: Separate preprocessing pipelines from model code
- **Error Handling**: Graceful handling of malformed data and model failures
- **Performance**: Profile data loading and model inference bottlenecks
- **Testing**: Unit tests for data transformations and model outputs

### IoT & Real-time Processing:
- **Sensor Data**: Validate sensor readings and handle missing data
- **Async Processing**: Use `asyncio` for concurrent sensor reading
- **Buffer Management**: Use `collections.deque` for efficient ring buffers
- **Communication**: Use standard protocols (HTTP, MQTT) with proper error handling
- **Edge Computing**: Minimize dependencies for resource-constrained environments

### Dependencies Philosophy:
- **Standard Library First**: Always check if standard library can solve the problem
- **Minimal Dependencies**: Each dependency must provide significant value
- **Popular Libraries Only**: numpy, pandas, scikit-learn when needed
- **Avoid Bloat**: Don't add libraries for single functions
- **Security**: Regularly audit dependencies with `uv audit`
