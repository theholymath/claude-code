---
allowed-tools: all
description: Verify code quality, run tests, and ensure production readiness
---

# 🚨🚨🚨 CRITICAL REQUIREMENT: FIX ALL ERRORS! 🚨🚨🚨

**THIS IS NOT A REPORTING TASK - THIS IS A FIXING TASK!**

When you run `/check`, you are REQUIRED to:

1. **IDENTIFY** all errors, warnings, and issues
2. **FIX EVERY SINGLE ONE** - not just report them!
3. **USE MULTIPLE AGENTS** to fix issues in parallel:
   - Spawn one agent to fix linting issues
   - Spawn another to fix test failures
   - Spawn more agents for different files/modules
   - Say: "I'll spawn multiple agents to fix all these issues in parallel"
4. **DO NOT STOP** until:
   - ✅ ALL linters pass with ZERO warnings
   - ✅ ALL tests pass
   - ✅ Build succeeds
   - ✅ EVERYTHING is GREEN

**FORBIDDEN BEHAVIORS:**
- ❌ "Here are the issues I found" → NO! FIX THEM!
- ❌ "The linter reports these problems" → NO! RESOLVE THEM!
- ❌ "Tests are failing because..." → NO! MAKE THEM PASS!
- ❌ Stopping after listing issues → NO! KEEP WORKING!

**MANDATORY WORKFLOW:**
```
1. Run checks → Find issues
2. IMMEDIATELY spawn agents to fix ALL issues
3. Re-run checks → Find remaining issues
4. Fix those too
5. REPEAT until EVERYTHING passes
```

**YOU ARE NOT DONE UNTIL:**
- All linters pass with zero warnings
- All tests pass successfully
- All builds complete without errors
- Everything shows green/passing status

---

🛑 **MANDATORY PRE-FLIGHT CHECK** 🛑
1. Re-read ~/.claude/CLAUDE.md RIGHT NOW
2. Check current TODO.md status
3. Verify you're not declaring "done" prematurely

Execute comprehensive quality checks with ZERO tolerance for excuses.

**FORBIDDEN EXCUSE PATTERNS:**
- "This is just stylistic" → NO, it's a requirement
- "Most remaining issues are minor" → NO, ALL issues must be fixed
- "This can be addressed later" → NO, fix it now
- "It's good enough" → NO, it must be perfect
- "The linter is being pedantic" → NO, the linter is right

Let me ultrathink about validating this codebase against our exceptional standards.

🚨 **REMEMBER: Hooks will verify EVERYTHING and block on violations!** 🚨

**Universal Quality Verification Protocol:**

**Step 0: Hook Status Check**
- Run `~/.claude/hooks/smart-lint.sh` directly to see current state
- If ANY issues exist, they MUST be fixed before proceeding
- Check `~/.claude/hooks/violation-status.sh` if it exists

**Step 1: Pre-Check Analysis**
- Review recent changes to understand scope
- Identify which tests should be affected
- Check for any outstanding TODOs or temporary code

**Step 2: Python Quality Pipeline**
Run Python quality checks using `uv`:
- `uv run black --check .` - Code formatting check
- `uv run ruff check .` - Fast linting and code quality
- `uv run mypy .` - Type checking
- `uv run pytest --cov` - Tests with coverage
- `uv audit` - Security vulnerability scanning

**Universal Requirements:**
- ZERO warnings across ALL linters (ruff, mypy, black)
- ZERO disabled linter rules without documented justification
- ZERO "# noqa" or suppression comments without explanation
- ZERO formatting issues (all code must be black-formatted)
- ZERO type: ignore comments without specific type annotations

**For Python projects specifically:**
- ZERO warnings from ruff (all checks enabled)
- No disabled linter rules without explicit justification
- No use of `import *` or global variables
- No `# noqa` comments unless absolutely necessary with explanation
- Proper exception handling with context
- Type hints on all functions and methods
- Consistent naming following PEP 8 conventions
- No mutable default arguments

**Step 3: Test Verification**
Run `uv run pytest` and ensure:
- ALL tests pass without flakiness
- Test coverage is meaningful (not just high numbers)
- Parametrized tests for complex logic
- No skipped tests without justification
- Performance tests for critical data pipelines
- Tests actually test behavior, not implementation details
- Test data is properly isolated and cleaned up

**Python Quality Checklist:**
- [ ] No `import *` or global variables - explicit imports everywhere
- [ ] Simple exception handling - no complex hierarchies
- [ ] Early returns to reduce nesting
- [ ] Meaningful variable names (user_id not id)
- [ ] Proper type hints on all functions
- [ ] No resource leaks (use context managers)
- [ ] Context managers for file/connection cleanup
- [ ] No race conditions (test with threading if applicable)
- [ ] No busy waiting - use asyncio for concurrency
- [ ] Async/await patterns instead of threading for I/O

**Code Hygiene Verification:**
- [ ] All public functions have docstrings
- [ ] No commented-out code blocks
- [ ] No debugging print statements (use logging instead)
- [ ] No placeholder implementations or TODOs
- [ ] Consistent formatting (black)
- [ ] Dependencies are actually used (check with `uv tree`)
- [ ] No circular imports
- [ ] Jupyter notebooks have cleared outputs

**Security Audit:**
- [ ] Input validation on all external data (use dataclasses with validation)
- [ ] SQL queries use parameterized statements
- [ ] Crypto operations use `secrets` module
- [ ] No hardcoded secrets or credentials
- [ ] Proper file permission checks with `pathlib`
- [ ] Rate limiting for API endpoints
- [ ] ML model input sanitization

**Performance Verification:**
- [ ] No obvious N+1 queries
- [ ] Efficient data structures (use numpy arrays for numeric data)
- [ ] Async operations where beneficial
- [ ] Connection pooling configured
- [ ] No unnecessary object creation in hot paths
- [ ] No busy-wait loops consuming CPU
- [ ] Async/await used for efficient I/O coordination
- [ ] Proper memory management for large datasets

**Scientific Computing & ML/AI Verification:**
- [ ] Reproducible results (fixed random seeds)
- [ ] Data validation (shape, type, range checks)
- [ ] Model versioning and experiment tracking
- [ ] Proper handling of missing/invalid data
- [ ] Memory-efficient data loading for large datasets
- [ ] Cross-validation for model evaluation
- [ ] Input sanitization for model inference
- [ ] Notebook outputs cleared before commit
- [ ] Data preprocessing pipelines are testable
- [ ] Error handling for sensor data and IoT failures

**Failure Response Protocol:**
When issues are found:
1. **IMMEDIATELY SPAWN AGENTS** to fix issues in parallel:
   ```
   "I found 15 linting issues and 3 test failures. I'll spawn agents to fix these:
   - Agent 1: Fix linting issues in files A, B, C
   - Agent 2: Fix linting issues in files D, E, F  
   - Agent 3: Fix the failing tests
   Let me tackle all of these in parallel..."
   ```
2. **FIX EVERYTHING** - Address EVERY issue, no matter how "minor"
3. **VERIFY** - Re-run all checks after fixes
4. **REPEAT** - If new issues found, spawn more agents and fix those too
5. **NO STOPPING** - Keep working until ALL checks show ✅ GREEN
6. **NO EXCUSES** - Common invalid excuses:
   - "It's just formatting" → Auto-format it NOW
   - "It's a false positive" → Prove it or fix it NOW
   - "It works fine" → Working isn't enough, fix it NOW
   - "Other code does this" → Fix that too NOW
7. **ESCALATE** - Only ask for help if truly blocked after attempting fixes

**Final Verification:**
The code is ready when:
✓ make lint: PASSES with zero warnings
✓ make test: PASSES all tests
✓ go test -race: NO race conditions
✓ All checklist items verified
✓ Feature works end-to-end in realistic scenarios
✓ Error paths tested and handle gracefully

**Final Commitment:**
I will now execute EVERY check listed above and FIX ALL ISSUES. I will:
- ✅ Run all checks to identify issues
- ✅ SPAWN MULTIPLE AGENTS to fix issues in parallel
- ✅ Keep working until EVERYTHING passes
- ✅ Not stop until all checks show passing status

I will NOT:
- ❌ Just report issues without fixing them
- ❌ Skip any checks
- ❌ Rationalize away issues
- ❌ Declare "good enough"
- ❌ Stop at "mostly passing"
- ❌ Stop working while ANY issues remain

**REMEMBER: This is a FIXING task, not a reporting task!**

The code is ready ONLY when every single check shows ✅ GREEN.

**Executing comprehensive validation and FIXING ALL ISSUES NOW...**
