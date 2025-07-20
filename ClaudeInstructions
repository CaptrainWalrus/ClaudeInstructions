# Claude Instructions - Collaborative Design Philosophy

*Your guidelines for effective Claude collaboration based on real-world trading system development*

## Core Interaction Principles

### 1. Systematic Code Protocol
- **Analysis → Planning → Incremental Changes → Testing**
- Always analyze existing architecture before making changes
- Use TodoWrite tool to plan and track multi-step tasks
- Make incremental changes with testing at each step
- Verify no breakage of existing functionality

### 2. Modularity & Preservation First
- **Break complex logic into atomic parts**
- Prefer importing/extending over modifying working components
- Keep files under 500 lines, organize into logical directories
- **Preserve what works** - don't modify functioning components unnecessarily
- Analyze cascading effects before making any changes

### 3. Dependency-Aware Development
- Always understand the full dependency chain before changes
- Test all affected components when making modifications
- **No synthetic data or fallbacks that hide mistakes**
- Verify real data flow from source to destination

### 4. Confirmation & Clarity Requirements
- **Always confirm what files/changes are being made**
- Ask detailed questions to remove ambiguities before proceeding
- Provide step-by-step reasoning for complex decisions
- Break down problems and evaluate trade-offs explicitly

## Technical Environment Standards

### Windows Development Environment
- Use PowerShell for command execution
- Separate multiple commands with `;` 
- Handle path spaces with proper quoting
- Respect Windows file system conventions

### Server Management
- **Don't start servers unless explicitly requested**
- Understand service dependencies and port assignments
- Use existing service architecture (MI:3002, ME:5000, RF:3009, etc.)

### Logging & Debugging Standards
- Unless specifically asked to log to file, assume "log" means terminal/console output
- Provide clear, actionable error messages
- Include context in debugging output
- Track data flow through service chains

## Planning & Memory Management

### Session Continuity
- **Keep hard files in workspace/ for /plan references**
- Store planning documents as physical files to persist across Claude Code sessions
- Maintain workspace/ directory for all planning materials
- Use claude_memory.md for chronological development thoughts

### Task Management Philosophy
- Use TodoWrite proactively for complex multi-step tasks
- Mark todos as completed immediately after finishing
- Only have ONE task in_progress at any time
- Break complex tasks into specific, actionable items

### Documentation Requirements
- Focus on architectural decisions and their reasoning
- Document experimental code that may seem "unused"
- Explain the purpose behind preserving optionality
- Maintain context for future development iterations

## Trading System Development Philosophy

### Experimental Nature Acceptance
- **Trading systems are never "complete" by design**
- Preserve unused code and variables for future experimentation
- Uncertainty in trading requires maintaining optionality
- Rapid iteration over architectural perfection

### Risk-First Development
- Always consider financial risk implications of code changes
- Implement fail-safe patterns (reject on errors, timeouts)
- Validate data integrity through the entire pipeline
- Maintain audit trails for all trading decisions

### Real-Time System Considerations
- Understand latency implications of code changes
- Preserve real-time data flow integrity
- Test with actual market conditions, not synthetic data
- Validate temporal accuracy (bar time vs server time)

## Code Quality Standards

### Interface Contracts
- Understand implicit agreements between services
- Validate data structures and formats at boundaries
- Implement self-validating distributed contracts when needed
- Catch silent failures and data corruption

### Error Handling Philosophy
- Traditional error handling misses silent failures
- Implement intelligent monitoring for data pattern anomalies
- Understand expected patterns and detect deviations
- Provide meaningful error messages with context

### Performance Considerations
- Understand the real-time nature of trading systems
- Optimize for latency-sensitive operations
- Consider memory usage in long-running processes
- Profile bottlenecks in data processing chains

## Architectural Evolution Patterns

### From Static to Adaptive
- **Evolution**: Static rule-based → Adaptive learning systems
- Implement graduated feature importance over fixed thresholds
- Use historical pattern analysis for decision making
- Build systems that learn from outcomes

### Feature Engineering Excellence
- Understand the 94+ feature engineering pipeline
- Respect feature graduation and importance ranking
- Implement range-based intelligence over similarity matching
- Consider position size normalization in all PnL calculations

### Storage & Retrieval Design
- Implement three-state data routing (TRAINING/RECENT/OUT_OF_SAMPLE)
- Use LanceDB for vector similarity, JSON for performance tracking
- Normalize PnL calculations to per-contract values
- Maintain temporal accuracy with bar-time based updates

## Communication Style

### Response Efficiency
- **Minimize output tokens while maintaining quality**
- Address specific queries directly without unnecessary preamble
- Avoid tangential information unless critical
- Keep responses short for CLI interface display

### Technical Precision
- Use exact technical terminology
- Reference specific file paths and line numbers when relevant
- Provide code examples that follow existing patterns
- Explain complex concepts with clear analogies

## Key Success Patterns

### What Works Well
1. **Incremental development** with continuous validation
2. **Feature-first architecture** that supports experimentation
3. **Real-time feedback loops** for continuous learning
4. **Hybrid human-AI decision making** with override capabilities
5. **Comprehensive logging** that tracks decision reasoning

### What To Avoid
1. **Premature optimization** over working prototypes
2. **Rigid architectures** that limit experimentation
3. **Synthetic data** that masks real-world problems
4. **Breaking working components** without clear necessity
5. **Starting services** without explicit permission

## Historical Context Awareness

This instruction set evolved from building a sophisticated algorithmic trading system that transformed from:
- Static RF meta-labeling → Adaptive agentic memory
- Similarity matching → Range-based intelligence → Gaussian Process uncertainty modeling
- Fixed risk parameters → Dynamic risk adjustment based on graduated features

The system handles real-time market data processing, 94+ feature engineering, pattern recognition, and adaptive risk management - all while maintaining the flexibility needed for continuous trading research.

---

*"In trading, uncertainty is the only certainty. Code should reflect that reality - built for experimentation, learning, and continuous adaptation rather than rigid architectural perfection."*
