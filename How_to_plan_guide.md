# HOW TO PLAN GUIDE

## Overview

This guide establishes the standard approach for creating architectural plans. All plans should follow these principles to ensure consistency, manageability, and successful implementation.

## Core Planning Principles

### 1. **Manageability First**
- Break complex systems into discrete, manageable phases
- Each phase should deliver measurable value
- Avoid "big bang" implementations
- Prefer incremental rollouts with validation at each step

### 2. **Pre-defined Structure**
- Use consistent document structure across all plans
- Include clear sections for Overview, Architecture, Implementation, and Status
- Define success criteria upfront
- Track implementation progress inline

### 3. **Integration Over Modification**
- Identify minimal hooks needed in existing code
- Prefer importing new modules over editing existing files
- Document exactly which files need modification and why
- Keep modifications surgical and reversible

### 4. **File Size Discipline**
- Target maximum 500 lines per file
- Plan file splitting strategy upfront
- Use clear module boundaries
- Document inter-module dependencies

## Standard Plan Document Structure

### 1. Overview Section
```markdown
## Overview

[Brief description of what the system/feature does]

## Core Concept

### Current Approach (if refactoring)
- [How it works today]
- [Key limitations]

### Proposed Approach
- [How it will work]
- [Key improvements]
```

### 2. Architecture Section
```markdown
## Architecture

### Components
1. **Component Name**
   - Technology: [Tech stack]
   - Purpose: [What it does]
   - Key Responsibilities: [Bullet list]

### Data Flow
[ASCII or Mermaid diagram showing data flow]

### Integration Points
- **Service A → Service B**: [Description of integration]
- **Existing Hook Required**: [File:Function that needs modification]
```

### 3. Implementation Plan
```markdown
## Implementation Phases

### Phase 1: [Name] (Status: ⏳/✅/❌)
**Goal**: [What this phase achieves]

#### Tasks:
- [ ] Task 1.1: [Description]
  - File: `path/to/file.js`
  - Changes: [Specific changes needed]
  - Lines: ~50 (estimated)
  
- [ ] Task 1.2: [Description]
  - New File: `path/to/newfile.js`
  - Purpose: [What this file does]
  - Size: ~200 lines (planned)

✅ **Phase 1 Success Criteria:**
- [Measurable outcome 1]
- [Measurable outcome 2]
```

### 4. Integration Hooks Documentation
```markdown
## Integration Hooks

### Existing Code Modifications

#### Hook 1: [Purpose]
**File**: `existing/file.js`
**Function**: `existingFunction()`
**Change Type**: Add function call
**Implementation**:
```javascript
// EXISTING CODE
function existingFunction() {
  // ... existing logic ...
  
  // NEW: Integration hook
  if (newFeatureEnabled) {
    await newModule.process(data);
  }
}
```

### New Modules to Import
1. **Module**: `newFeatureModule`
   - Imported by: `existing/file.js`
   - Purpose: [Why this import is needed]
```

### 5. File Organization Plan
```markdown
## File Organization

### Service Directory Structure
```
new-service/
├── src/
│   ├── api/
│   │   └── routes/
│   │       └── mainRoutes.js (~150 lines)
│   │   ├── services/
│   │   │   ├── coreService.js (~300 lines)
│   │   │   └── helperService.js (~200 lines)
│   │   └── utils/
│   │       └── common.js (~100 lines)
│   └── server.js (~100 lines)
└── package.json
```

### File Size Planning
- **Large Logic Split Strategy**: 
  - If vectorCalculation > 500 lines, split into:
    - `vectorCore.js` (~250 lines) - Core calculation
    - `vectorHelpers.js` (~200 lines) - Helper functions
    - `vectorTypes.js` (~100 lines) - Type definitions
```

### 6. Status Tracking
```markdown
## Implementation Status

### Overall Progress: 60% Complete

### Phase Status:
- ✅ Phase 1: Foundation - COMPLETED
- ⏳ Phase 2: Core Logic - IN PROGRESS (75%)
- ⏯️ Phase 3: Integration - PLANNED
- ⏸️ Phase 4: Testing - BLOCKED (waiting for Phase 2)

### Recent Updates:
- **2024-01-15**: Completed integration hooks
- **2024-01-14**: Fixed vector dimension mismatch
- **2024-01-13**: Initial implementation started

### Known Issues:
- ❌ **Issue 1**: [Description] - [Proposed solution]
- ⚠️ **Risk 1**: [Description] - [Mitigation plan]
```

## Best Practices for Planning

### 1. **Start with Minimal Viable Flow**
```markdown
1. **Core Data Pipeline First**
   - Establish end-to-end connectivity
   - Use simple test data
   - Verify basic flow works
   
2. **Add Processing Logic**
   - Implement core algorithms
   - Add error handling
   - Validate outputs
   
3. **Enhance with Features**
   - Add optimizations
   - Implement edge cases
   - Polish user experience
```

### 2. **Document Integration Points Clearly**
```markdown
### Integration with [Service Name]

**Minimal Changes Required**:
1. Add import: `const newModule = require('./newModule');`
2. Add hook in `processData()`: Call `newModule.enhance(data)`
3. No other modifications needed

**Data Contract**:
- Input: `{ instrument, timestamp, data: [...] }`
- Output: `{ enhanced: true, processedData: [...] }`
```

### 3. **Plan for Testing**
```markdown
### Testing Strategy

1. **Unit Tests** (per module)
   - `coreService.test.js` - Core logic validation
   - `integration.test.js` - Hook verification

2. **Integration Tests**
   - End-to-end flow with real services
   - Performance benchmarks
   - Error scenario validation
```

### 4. **Consider Deployment Early**
```markdown
### Deployment Considerations

1. **Environment Variables**
   - `NEW_SERVICE_PORT` - Default: 3500
   - `INTEGRATION_ENABLED` - Feature flag

2. **Dependencies**
   - Requires Service A to be running
   - Optional connection to Service B

3. **Resource Requirements**
   - Memory: ~512MB
   - CPU: Low (< 10% single core)
```

## Common Patterns to Follow

### 1. **Additive Architecture**
- New services that don't disrupt existing ones
- Feature flags for gradual rollout
- Backward compatibility maintained

### 2. **Cache-First Design**
- Use in-memory caches to reduce external calls
- Plan cache invalidation strategy
- Document cache size limits

### 3. **Async Processing**
- Acknowledge quickly, process asynchronously
- Use queues for reliability
- Plan for failure scenarios

### 4. **Monitoring Integration**
- Plan logging strategy upfront
- Include performance metrics
- Design for observability

## Anti-Patterns to Avoid

### 1. **Don't Create Monolithic Plans**
❌ Single 50-page document covering everything
✅ Modular plans with clear phases

### 2. **Don't Modify Core Logic Unnecessarily**
❌ Rewriting existing services
✅ Adding hooks and importing new modules

### 3. **Don't Ignore File Size**
❌ 2000-line service files
✅ Well-organized modules under 500 lines

### 4. **Don't Skip Status Updates**
❌ Plans that become stale
✅ Living documents with progress tracking

## Template Checklist

Before finalizing any plan, ensure:

- [ ] Clear phases with success criteria
- [ ] Integration hooks explicitly documented
- [ ] File organization planned (all files < 500 lines)
- [ ] Status tracking section included
- [ ] Testing strategy defined
- [ ] Deployment considerations addressed
- [ ] ASCII/Mermaid diagrams for data flow
- [ ] Code examples for critical integrations

## Example Plans to Reference

1. **SimpliFACTOR.md** - Excellent phased refactoring plan
2. **divergence-visualizer-plan.md** - Good example of additive architecture
3. **new_divergence_refactor.md** - Shows how to enhance existing systems
4. **pattern-discovery-engine.md** - Demonstrates conceptual planning

## Conclusion

Following this guide ensures our architectural plans are:
- **Actionable**: Clear steps with measurable outcomes
- **Manageable**: Broken into digestible phases
- **Maintainable**: Respecting file size and modularity
- **Trackable**: Living documents showing progress

Remember: A good plan evolves with implementation but maintains its core structure and principles throughout the project lifecycle. 
