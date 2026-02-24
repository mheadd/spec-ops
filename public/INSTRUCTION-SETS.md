# SpecOps Instruction Set Examples
## Building a Collaborative Library of AI Agent Skills for Legacy Modernization

## Table of Contents
- [Introduction](#introduction)
- [Evidence Base](#evidence-base)
- [The Evolving Nature of Instruction Sets](#the-evolving-nature-of-instruction-sets)
  - [Instruction Sets Are a Work in Progress](#instruction-sets-are-a-work-in-progress)
  - [Parallel Development](#parallel-development)
- [Categories of Instruction Sets](#categories-of-instruction-sets)
- [Instruction Set Maturity Levels](#instruction-set-maturity-levels)
- [Instruction Set Design Principles](#instruction-set-design-principles)
- [Opportunities for Collaboration](#opportunities-for-collaboration)
  - [Who Can Contribute Instruction Sets?](#who-can-contribute-instruction-sets)
  - [Models for Collaboration](#models-for-collaboration)
- [Sharing Instruction Sets Across Governments](#sharing-instruction-sets-across-governments)
  - [Why This Works for Government](#why-this-works-for-government)
  - [What Can Be Shared](#what-can-be-shared)
- [Example Instruction Sets](#example-instruction-sets)
- [Getting Started: Building Your Instruction Set Library](#getting-started-building-your-instruction-set-library)
- [Contributing to the SpecOps Instruction Library](#contributing-to-the-specops-instruction-library)
- [Instruction Set Repository Structure](#instruction-set-repository-structure)
- [Measuring Instruction Set Effectiveness](#measuring-instruction-set-effectiveness)
- [Conclusion: Building Together](#conclusion-building-together)
- [Getting Involved](#getting-involved)

---

## Introduction

AI agent instruction sets—often called "skills" or "custom instructions"—are one of the most critical and reusable components of the SpecOps methodology. These instruction sets guide AI coding agents in understanding legacy code, generating accurate specifications, and implementing modern replacements.

**A key insight: Instruction sets are more portable and sharable than code.**

Unlike actual software code, which is tightly coupled to specific systems and contexts, instruction sets encode knowledge and patterns that can be applied across different organizations and projects. A well-crafted instruction set for understanding COBOL code works whether you're modernizing a benefits system in California or a tax system in New York.

This creates enormous opportunity for collaboration and knowledge sharing across government agencies, between states, and even internationally.

---

## Evidence Base

The case for human-curated instruction sets is supported by early empirical research. A 2026 benchmarking study (Li et al., "SkillsBench: Benchmarking the Effect of Skills on LLM Agent Code Generation," arXiv:2602.12670) tested curated Skills against no-Skills baselines across 86 tasks and thousands of agent trajectories. The findings align with several core SpecOps assumptions:

- **Human-curated instruction sets meaningfully improve agent performance.** Curated Skills raised average pass rates substantially, with the largest gains in specialized domains where procedural knowledge is underrepresented in model training data.
- **Not all instruction sets help equally.** Effects varied widely by domain, and a meaningful share of tasks showed negative deltas — instruction sets that actively hurt performance. This underscores the need for testing and iteration, not blind adoption.
- **Focused instruction sets outperform comprehensive ones.** Sets with 2–3 targeted modules consistently outperformed broad documentation packages. More content is not better content.
- **Self-generated Skills provide no benefit on average.** When agents were prompted to generate their own procedural knowledge, the resulting instructions offered negligible or negative improvement. Models cannot reliably author the procedural knowledge they benefit from consuming. This is not a temporary limitation to wait out — it is the structural argument for why human-authored instruction sets are worth the investment.
- **Smaller models with good instruction sets can match larger models without them.** This has direct implications for cost and accessibility in government settings.

This is early evidence in a fast-moving research area, not settled science. But the direction is clear: curated, human-authored procedural knowledge makes AI agents materially more capable — and doing it well requires deliberate effort, not automation.

---

## The Evolving Nature of Instruction Sets

### Instruction Sets Are a Work in Progress

**Important**: When starting a SpecOps modernization project, you likely won't have all the instruction sets you need. This is normal and expected. Instruction sets will be:

- **Developed iteratively** as you learn what works
- **Refined continuously** based on AI agent performance
- **Created in parallel** with specification generation
- **Contributed from multiple sources** both inside and outside your core team
- **Shared and improved** across the SpecOps community

**You don't need perfect instruction sets to start.** Begin with basic instructions, learn from experience, and improve as you go.

### Parallel Development

Instruction set development can happen in parallel with other SpecOps phases:

**During Discovery**: Begin identifying needed instruction sets
**During Specification Generation**: Create and refine instructions as you encounter patterns
**Ongoing**: Continuously improve based on results
**Outside the Project**: Community members can contribute without being on the core team

This parallel approach means:
- Core team isn't blocked waiting for perfect instructions
- Domain experts can contribute instruction sets without technical expertise
- External contributors can help without access to legacy systems
- The instruction library grows organically over time

---

## Categories of Instruction Sets

SpecOps requires several types of instruction sets, each serving different purposes:

### 1. Legacy Code Comprehension Instructions

Help AI agents understand and document legacy systems:
- **COBOL Comprehension** - Understanding COBOL syntax, idioms, and patterns
- **Mainframe Environment** - JCL, CICS, batch processing, job scheduling
- **Legacy Databases** - VSAM, IMS, DB2 hierarchical structures
- **Legacy Application Servers** - CICS, WebSphere, Tuxedo
- **Procedural Language Skills** - PL/I, RPG, Natural, Assembly
- **Data Structure Analysis** - Copybooks, record layouts, file structures

### 2. Specification Generation Instructions

Guide AI in creating well-structured specifications:
- **Specification Structure** - Organizing specifications consistently
- **Plain Language Writing** - Making technical content accessible
- **Business Rule Extraction** - Separating logic from implementation
- **Edge Case Identification** - Recognizing and documenting exceptions
- **Cross-Reference Creation** - Linking related specifications
- **Uncertainty Documentation** - Flagging ambiguities for human review

### 3. Domain-Specific Instructions

Provide context for specific government domains:
- **Benefits Eligibility Rules** - SNAP, TANF, Medicaid, etc.
- **Tax Calculation Logic** - Income tax, sales tax, property tax
- **Licensing and Permitting** - Application workflows, approval processes
- **Financial Systems** - Accounting rules, budget controls, audit requirements
- **Regulatory Compliance** - Industry-specific regulations and standards

### 4. Modern Implementation Instructions

Guide generation of modern code from specifications:
- **Cloud-Native Patterns** - Microservices, serverless, containers
- **API Design** - RESTful patterns, GraphQL, async messaging
- **Database Modeling** - Relational design, NoSQL patterns
- **Security Implementation** - Authentication, authorization, encryption
- **Testing Approach** - Test structure, coverage requirements

### 5. Government-Specific Instructions

Address unique government requirements:
- **Section 508 Compliance** - Accessibility requirements
- **FISMA/FedRAMP Security** - Security control implementation
- **Plain Language Act** - Clear communication requirements
- **ATO Documentation** - Security authorization artifacts
- **U.S. Web Design System** - Government UI standards
- **Open Data Standards** - DCAT-US, Project Open Data metadata

---

## Instruction Set Maturity Levels

Not all instruction sets need to be fully mature to be useful. We can think of them at different maturity levels:

### Level 1: Basic Instructions (Sufficient to Start)
- General guidance for the task
- Common patterns to look for
- Examples of desired output
- Known pitfalls to avoid

**Example**: "When analyzing COBOL code, identify PERFORM statements as function calls and MOVE statements as assignments."

### Level 2: Refined Instructions (Improved Through Use)
- Specific patterns for common scenarios
- Detailed examples from actual use
- Handling of edge cases
- Integration with other instruction sets

**Example**: "COBOL PERFORM statements with THRU clauses execute a range of paragraphs. Document these as compound operations in the specification..."

### Level 3: Mature Instructions (Refined and Focused)
- Distilled pattern library targeting the highest-value patterns
- Carefully selected examples and test cases — enough to be clear, not so many as to overwhelm
- Integration with multiple tools and workflows
- Community validation and contributions
- Version history and improvements documented
- Deliberately scoped to 2–3 focused modules rather than exhaustive documentation

The goal at Level 3 is not volume but precision — focused guidance that covers the patterns that matter without adding overhead that obscures them. Comprehensive documentation can actually degrade agent performance compared to concise, well-structured instruction sets. Resist the urge to keep adding; instead, edit ruthlessly.

**Example**: A COBOL business logic extraction skill distilled to its most effective patterns — tested across dozens of systems, trimmed to the guidance that actually moves the needle, with contributions from multiple organizations.

**Start with Level 1, evolve to Level 3 through practice and community contribution. But remember: the path from Level 2 to Level 3 is about removing what doesn't help as much as adding what does.**

---

## Instruction Set Design Principles

Not all instruction sets are created equal. How you structure and scope them matters as much as what they contain. The following principles should guide instruction set development:

### Focus Beats Breadth

Instruction sets with 2–3 focused modules consistently outperform broad, comprehensive documentation packages. When an instruction set tries to cover an entire domain, it introduces noise that can actually degrade agent performance — sometimes to worse than having no instruction set at all.

**Do**: Create a focused instruction set for COBOL copybook analysis with clear patterns and examples.
**Don't**: Create a single instruction set that covers all of COBOL comprehension, copybook analysis, JCL processing, and batch job documentation.

### Working Examples Over Exhaustive Explanation

Concrete, well-chosen examples are more effective than lengthy explanations of every possible scenario. A few realistic input/output pairs teach an agent more than pages of abstract guidance.

### Target Procedural Gaps, Not General Knowledge

Instruction sets should focus on specialized procedural knowledge that the model is unlikely to have — not general programming concepts or widely documented patterns. An agent already knows what a FOR loop does; it may not know how a state's categorical eligibility rules interact with federal SNAP guidelines.

The domains where instruction sets provide the most dramatic improvement are exactly those where procedural knowledge is most specialized and least represented in training data.

### Match Scope to Task Class

Instruction sets should be scoped to a specific class of tasks, not an entire domain. A skill for "extracting business rules from COBOL conditional logic" is more effective than a skill for "understanding COBOL." The narrower the task alignment, the better the performance.

### Test and Measure — Some Instructions Hurt

A meaningful share of instruction sets will make agent output worse, not better. This isn't a failure of the approach — it's a reminder that instruction sets must be tested against actual tasks and refined or removed when they don't help. Treat instruction set development with the same rigor you'd apply to code: test, measure, iterate.

### Human Authorship Is Not Optional

AI agents prompted to generate their own procedural knowledge produce instructions that offer negligible or negative benefit on average. Effective instruction sets require human expertise — domain knowledge, editorial judgment, and iterative refinement based on observed agent performance. This is a feature of the approach, not a limitation: it's precisely why the investment in human curation pays off.

---

## Opportunities for Collaboration

### Who Can Contribute Instruction Sets?

**Core SpecOps Team Members**:
- Create instruction sets as they encounter patterns
- Refine based on direct experience with AI agent output
- Test and validate effectiveness

**Domain Experts Outside the Team**:
- Contribute domain-specific knowledge
- Provide examples of business rules and patterns
- Review and validate domain instruction sets
- Don't need to be on the core team or have technical expertise

**Legacy System Specialists**:
- Deep expertise in specific legacy platforms
- Can create comprehensive comprehension instructions
- May be consultants or retired experts
- Contribute without being full-time team members

**Other Government Agencies**:
- Share instruction sets across agencies
- Collaborate on common platforms (COBOL, mainframes)
- Pool resources for mature instruction development
- Reduce duplication of effort

**Civic Tech and Open Source Communities**:
- External technologists who want to help government
- Can develop instruction sets without access to systems
- Review and improve existing instructions
- Create instruction sets for common legacy platforms

### Models for Collaboration

**Agency-to-Agency Sharing**:
- Federal agencies share instruction sets through shared repositories
- State governments collaborate on common legacy platforms
- Local governments pool resources for instruction development

**Public-Private Partnership**:
- Vendors who work with government contribute instruction sets
- Former government employees share knowledge
- Academic institutions contribute research and patterns

**Open Source Community Model**:
- Public GitHub repository for instruction sets
- Community reviews and improvements
- Forking and customization for specific needs
- Pull requests for new contributions

---

## Sharing Instruction Sets Across Governments

### Why This Works for Government

**Common Legacy Platforms**: Many governments use the same legacy technologies
- COBOL is COBOL everywhere
- Mainframe patterns are similar across organizations
- Database structures follow common patterns
- Business logic differs, but technical patterns don't

**Similar Domains**: Government functions are often parallel
- Benefits eligibility across states
- Tax systems across jurisdictions
- Licensing and permitting processes
- Financial management systems

**Shared Challenges**: Common problems create shared solutions
- Retiring workforce and knowledge loss
- Compliance and security requirements
- Budget constraints
- Need for modernization

**Low Barriers to Sharing**: Instruction sets are inherently shareable
- No proprietary business logic
- No sensitive data
- Just patterns and knowledge
- Easy to customize for local context

**High-Impact Domains**: Government legacy domains are precisely where instruction sets provide the greatest benefit. Benefits administration, tax processing, licensing, unemployment insurance — these areas involve specialized procedural knowledge that is underrepresented in model training data. The more specialized and domain-specific the knowledge, the larger the performance improvement when it's captured in a well-crafted instruction set. Government agencies working in these domains stand to gain the most from investing in curated instruction sets.

### What Can Be Shared

**Highly Shareable** (minimal customization needed):
- Legacy language comprehension (COBOL, RPG, etc.)
- Legacy platform knowledge (mainframes, databases)
- Specification structure and format
- Testing and validation patterns
- Security and compliance requirements
- Plain language and accessibility guidelines

**Moderately Shareable** (some customization needed):
- Domain-specific patterns (benefits, tax, licensing)
- Modern implementation patterns (may vary by tech choices)
- Organizational standards and conventions

**Less Shareable** (highly specific):
- Instructions tied to specific legacy system architecture
- Organization-specific business rules
- Custom integrations and dependencies

### Building a Shared Instruction Library

**Central Repository**:
- GitHub organization for government instruction sets
- Organized by category (language, platform, domain)
- Clear licensing (public domain or permissive open source)
- Quality standards and review process

**Contribution Process**:
- Template for new instruction sets
- Testing and validation requirements
- Documentation standards
- Community review and approval

**Maintenance and Evolution**:
- Version control for instruction improvements
- Feedback mechanisms for users
- Regular updates as AI tools evolve
- Attribution to contributors

**Discovery and Reuse**:
- Searchable catalog of available instructions
- Usage examples and test cases
- Success stories from adopters
- Metrics on instruction effectiveness

---

## Example Instruction Sets

Below are examples of instruction sets at different maturity levels. These are templates and starting points, not fully developed skills.

### Example 1: COBOL Business Logic Extraction (Level 2 - Refined)

```markdown
# COBOL Business Logic Extraction Skill

## Purpose
Help AI agents identify and extract business logic from COBOL code, separating it from technical implementation details.

## Key Patterns to Recognize

### Business Rules
- IF-THEN-ELSE statements implementing eligibility or calculation rules
- EVALUATE statements acting as decision tables
- COMPUTE statements performing calculations
- Nested conditionals implementing complex rule hierarchies

### Technical Implementation (Separate from Business Logic)
- File I/O operations (READ, WRITE, OPEN, CLOSE)
- Error handling routines
- Loop control structures (PERFORM UNTIL)
- Data movement without transformation (MOVE A TO B)

## Extraction Guidelines

### For Conditional Logic:
1. Identify the condition being tested
2. State it in plain language (e.g., "If applicant income is below threshold...")
3. Describe the action taken (e.g., "...then flag as eligible")
4. Note any exceptions or special cases
5. Cross-reference related business rules

### For Calculations:
1. Describe what is being calculated
2. List the inputs and their sources
3. Explain the formula in business terms
4. Note any constants or thresholds
5. Identify rounding or precision requirements

### For Decision Tables:
1. List all possible values being evaluated
2. Document the action for each value
3. Note the default case if present
4. Explain business meaning of each branch

## Output Format
Generate specifications that:
- Lead with business purpose
- Separate "what" from "how"
- Use domain language, not technical jargon
- Include examples for complex rules
- Flag ambiguities or uncertainties

## Examples

**Input (COBOL)**:
```cobol
IF INCOME-AMOUNT < POVERTY-THRESHOLD
   MOVE 'ELIGIBLE' TO DETERMINATION-CODE
   COMPUTE BENEFIT-AMT = BASE-BENEFIT * FAMILY-SIZE
ELSE
   MOVE 'NOT-ELIGIBLE' TO DETERMINATION-CODE
   MOVE ZERO TO BENEFIT-AMT
END-IF
```

**Output (Specification)**:
```
Business Rule: Income-Based Eligibility Determination

If applicant's household income is below the federal poverty threshold:
- Mark application as eligible
- Calculate benefit amount as: base benefit × family size

If applicant's household income is at or above poverty threshold:
- Mark application as not eligible
- Set benefit amount to zero

Inputs:
- Household income (annual dollar amount)
- Federal poverty threshold (annual dollar amount, varies by year)
- Family size (number of household members)
- Base benefit (dollar amount per person)

Outputs:
- Eligibility determination (eligible/not eligible)
- Benefit amount (monthly dollar amount or zero)
```

## Common Pitfalls to Avoid
- Don't reproduce technical syntax in specifications
- Don't assume you understand business purpose without evidence
- Don't skip edge cases even if code seems straightforward
- Don't merge multiple distinct rules into one specification section
- Flag uncertainty rather than guessing at business intent

## Integration Notes
- Works with COBOL Comprehension skill for syntax understanding
- Feeds into Specification Structure skill for organization
- Outputs used by Domain-Specific skills for validation
```

---

### Example 2: Benefits Eligibility Domain Skill (Level 1 - Basic)

```markdown
# Benefits Eligibility Domain Skill

## Purpose
Provide AI agents with context about public benefits eligibility determination to improve specification accuracy.

## Key Concepts

### Common Eligibility Factors
- Income (household, individual, gross, net)
- Assets (countable vs. excluded)
- Household composition (size, relationships)
- Residency requirements
- Citizenship/immigration status
- Work requirements
- Age requirements
- Disability status

### Typical Eligibility Rules
- Income thresholds (often as percentage of Federal Poverty Level)
- Asset limits
- Categorical eligibility (automatic qualification based on other program participation)
- Deductions and disregards (amounts excluded from income calculation)
- Special circumstances (hardship, emergency situations)

### Important Distinctions
- Application vs. recertification rules
- Initial vs. ongoing eligibility
- Mandatory vs. optional rules
- Federal minimum vs. state options

## Specification Guidance

When documenting eligibility rules:
1. Specify whether rule is federal requirement or state option
2. Include effective dates if rules have changed
3. Note any exceptions or special circumstances
3. Reference policy source (statute, regulation, manual) if possible
4. Include examples showing rule application
5. Flag complex interactions between rules

## Terminology Standards
- Use "applicant" before approval, "participant" or "beneficiary" after
- Use "household" not "family" unless specifically defined in policy
- Specify whether income is monthly, annual, or other period
- Be explicit about whose income/assets are counted
- Use "determination" or "decision" not "calculation" for eligibility

## Common Edge Cases to Watch For
- Self-employment income calculations
- Student status and income disregards
- Vehicle asset exclusions
- Treatment of lump sum payments
- Verification requirements and self-declaration

## Red Flags Requiring Domain Expert Review
- Unclear effective date for rule changes
- Ambiguous treatment of specific income or asset types
- Complex interactions between multiple eligibility factors
- Inconsistency between different parts of the code
- References to external systems or data sources
```

---

### Example 3: Specification Structure Skill (Level 2 - Refined)

```markdown
# Specification Structure Skill

## Purpose
Ensure consistent organization and formatting of specifications across all components.

## Standard Specification Structure

### Component Specification Template

**1. Overview**
- Component name and identifier
- Purpose and responsibilities
- Position in overall system architecture
- Key stakeholders

**2. Business Context**
- What business need this component serves
- Who uses it and how
- What business processes it supports
- Relevant policies or regulations

**3. Inputs**
- Data received (structure, source, frequency)
- Events that trigger processing
- Dependencies on other components
- External system inputs

**4. Business Logic**
- Rules and decision points
- Calculations and formulas
- Validation requirements
- Exception handling
- Organized by logical grouping, not code structure

**5. Outputs**
- Data produced (structure, destination, frequency)
- Events triggered
- Side effects and state changes
- Reports or notifications generated

**6. Data Models**
- Internal data structures
- Database schemas
- File layouts
- Data relationships and constraints

**7. Integration Points**
- Other components this depends on
- Components that depend on this
- External system integrations
- APIs or interfaces exposed

**8. Non-Functional Requirements**
- Performance requirements
- Security and access control
- Audit and logging requirements
- Error handling approach

**9. Edge Cases and Exceptions**
- Unusual scenarios and how they're handled
- Known limitations
- Workarounds for specific situations
- Historical context if relevant

**10. Uncertainties and Questions**
- Areas where specification may be incomplete
- Ambiguities requiring domain expert clarification
- Assumptions made that need validation
- Technical decisions that need review

**11. Verification Status**
- Who has reviewed this specification
- What sections have been verified
- Outstanding issues or questions
- Approval status

**12. References**
- Related specifications
- Legacy code locations
- Policy documents
- External documentation

## Formatting Guidelines

### Headings
- Use clear, descriptive headings
- Nest logically (H1 > H2 > H3)
- Make headings scannable

### Content
- Write in present tense
- Use active voice
- Lead paragraphs with key information
- Keep paragraphs focused and concise
- Use bullet lists for items without priority order
- Use numbered lists for sequences or priority order

### Examples
- Include concrete examples for complex rules
- Use realistic data in examples
- Show both normal and edge cases
- Format examples consistently

### Cross-References
- Link to related specifications using standard format: [Component Name](link)
- Reference policy sources with citations
- Note dependencies explicitly
- Keep cross-references up to date

## Quality Checks

Before considering a specification complete:
- [ ] All required sections present (may be marked as "not applicable")
- [ ] Technical terms defined in glossary or explained
- [ ] Examples provided for complex logic
- [ ] Cross-references are accurate and working
- [ ] Verification status is current
- [ ] No placeholder text like "TBD" without explanation
- [ ] Formatting is consistent with other specifications

## Version Control

- Update version number when specification changes
- Document what changed and why
- Link changes to specific code changes or policy updates
- Maintain change history
```

---

### Example 4: Mainframe Batch Job Comprehension (Level 1 - Basic)

```markdown
# Mainframe Batch Job Comprehension Skill

## Purpose
Help AI agents understand mainframe batch processing patterns and document them in specifications.

## Key Concepts to Recognize

### JCL (Job Control Language)
- Job definitions and job steps
- Dataset definitions (DD statements)
- Program execution (EXEC statements)
- Conditional execution (IF/THEN/ELSE)
- Return code checking

### Batch Processing Patterns
- Sequential processing of records
- Sort/merge operations
- Report generation
- Data transformation and validation
- Multi-step workflows

### Data Flow
- Input files and their formats
- Intermediate work files
- Output files and reports
- Database updates
- Error and exception files

## Documentation Approach

### For Batch Jobs:
1. Describe the overall purpose of the job
2. List the input datasets and their sources
3. Document each step in the job
4. Explain data transformations
5. Note output datasets and their destinations
6. Describe error handling and restart logic

### For Each Job Step:
1. What program is executed
2. What inputs it consumes
3. What processing it performs
4. What outputs it produces
5. What happens if the step fails

## Common Patterns to Identify

**Data Validation Jobs**
- Read input file
- Validate each record
- Write good records to one file
- Write errors to exception file
- Generate validation report

**Data Transformation Jobs**
- Read input in one format
- Transform/calculate new values
- Write output in different format
- Update database with results

**Report Generation Jobs**
- Extract data from multiple sources
- Perform calculations or aggregations
- Format for human readability
- Output to report file or printer

**Month-End/Year-End Processing**
- Read transaction data
- Update summary tables
- Generate period-end reports
- Archive processed data

## Red Flags

Watch for:
- Jobs with complex restart/recovery logic
- Dependencies on job schedule or timing
- Manual intervention points
- Undocumented data sources
- Assumptions about data formats
```

---

## Getting Started: Building Your Instruction Set Library

### Phase 1: Identify What You Need (Week 1)

**Assess Your Legacy System**:
- What languages? (COBOL, PL/I, etc.)
- What platforms? (Mainframe, midrange, etc.)
- What databases? (DB2, IMS, VSAM, etc.)
- What domains? (Benefits, tax, financial, etc.)

**Search for Existing Instructions**:
- Check the SpecOps community library
- Ask other agencies what they have
- Look for relevant open source projects
- Contact vendors or consultants
- **Search public repositories**: Tens of thousands of agent Skills are now publicly available in repositories tagged with agent-skills conventions (e.g., on GitHub). Before building instruction sets from scratch, search for existing work that can be adapted. The community model this document envisions is already emerging in practice — leverage it.

**Prioritize Development**:
- What do you need immediately?
- What can you find/adapt?
- What must be custom-built?
- What can wait until later?

### Phase 2: Start with Basics (Weeks 2-4)

**Create Level 1 Instructions**:
- Basic comprehension for your legacy language
- General specification structure guidance
- Simple domain concepts
- Test with AI agents on sample code

**Iterate Quickly**:
- Try instruction set → Review output → Refine instructions
- Don't aim for perfection
- Get something working, then improve it
- Document what works and what doesn't

### Phase 3: Refine Through Use (Ongoing)

**Learn from Experience**:
- Track which instructions produce good results
- Note patterns that AI agents miss
- Document ambiguities and how to handle them
- Build library of examples

**Share and Collaborate**:
- Publish instruction sets to shared repository
- Get feedback from other teams
- Incorporate improvements from community
- Contribute back refinements

### Phase 4: Mature and Expand (Months 3-12)

**Develop Comprehensive Skills**:
- Expand pattern libraries
- Add more examples and edge cases
- Create domain-specific variations
- Document integration patterns

**Enable Community Contribution**:
- Create contribution guidelines
- Establish quality standards
- Set up review process
- Recognize contributors

---

## Contributing to the SpecOps Instruction Library

### How to Contribute

**1. Create Your Instruction Set**
- Follow the standard template
- Include clear examples
- Test with AI agents
- Document effectiveness

**2. Document Your Experience**
- What system did you use it on?
- What AI agents did you test with?
- What results did you see?
- What issues did you encounter?

**3. Submit to Community**
- Open pull request in shared repository
- Provide context in PR description
- Include test cases if applicable
- Respond to review feedback

**4. Maintain and Improve**
- Update based on community feedback
- Respond to issues raised by users
- Incorporate improvements from others
- Keep documentation current

### What Makes a Good Contribution

**Clear Purpose**: Explains what the instruction set does and when to use it
**Well-Tested**: Validated on real legacy code with multiple AI agents
**Good Examples**: Includes concrete before/after examples
**Properly Scoped**: Focused on specific task, not trying to do everything
**Well-Documented**: Others can understand and use it without your help

### Contribution License

All instruction sets contributed to the SpecOps community library should be:
- **Public domain** or **permissive open source** (MIT, Apache, etc.)
- **Free for any use** including commercial and government
- **Attributed to contributors** but not requiring permission for use
- **Modifiable and improvable** by anyone

This ensures maximum reuse and adaptation across government agencies.

---

## Instruction Set Repository Structure

Proposed organization for a shared instruction library:

```
specops-instructions/
├── README.md
├── CONTRIBUTING.md
├── LICENSE
├── catalog.md (searchable index)
│
├── legacy-languages/
│   ├── cobol/
│   │   ├── basic-comprehension.md
│   │   ├── business-logic-extraction.md
│   │   ├── copybook-analysis.md
│   │   └── examples/
│   ├── rpg/
│   ├── pl1/
│   └── natural/
│
├── legacy-platforms/
│   ├── mainframe/
│   │   ├── jcl-comprehension.md
│   │   ├── cics-analysis.md
│   │   ├── batch-processing.md
│   │   └── examples/
│   ├── db2/
│   ├── ims/
│   └── vsam/
│
├── domains/
│   ├── benefits/
│   │   ├── eligibility-rules.md
│   │   ├── benefit-calculation.md
│   │   └── appeals-processing.md
│   ├── tax/
│   ├── licensing/
│   └── financial/
│
├── specification/
│   ├── structure-standards.md
│   ├── plain-language.md
│   ├── cross-referencing.md
│   └── examples/
│
├── implementation/
│   ├── cloud-native-patterns.md
│   ├── api-design.md
│   ├── security-implementation.md
│   └── testing-approach.md
│
├── government-specific/
│   ├── section-508.md
│   ├── fisma-fedramp.md
│   ├── plain-writing-act.md
│   └── uswds.md
│
└── templates/
    ├── instruction-set-template.md
    ├── contribution-guide.md
    └── testing-guide.md
```

---

## Measuring Instruction Set Effectiveness

Track these metrics to evaluate and improve instruction sets:

### Quality Metrics
- **Accuracy Rate**: How often AI output matches expert review
- **Completeness**: Percentage of patterns successfully captured
- **Clarity**: How many clarification questions needed during verification
- **Consistency**: Variance in output across different AI agents

### Efficiency Metrics
- **Time Savings**: Reduction in manual specification writing time
- **Revision Cycles**: How many iterations needed to reach acceptable quality
- **Reuse Rate**: How often instruction sets are used across projects
- **Community Adoption**: Number of organizations using the instruction set

### Feedback Metrics
- **User Ratings**: Satisfaction scores from teams using instructions
- **Issue Reports**: Bug reports or improvement suggestions
- **Contribution Rate**: Community improvements and enhancements
- **Success Stories**: Documented wins using the instruction set

---

## Conclusion: Building Together

Instruction sets are the reusable knowledge layer that makes SpecOps practical at scale. Unlike proprietary code or sensitive data, instruction sets can and should be widely shared across government agencies and the broader community.

**Key Principles**:

1. **Start Simple**: Basic instructions are better than no instructions
2. **Iterate Quickly**: Refine based on real use, not speculation
3. **Share Openly**: Make instruction sets available to others
4. **Contribute Back**: Improve shared instructions with your learnings
5. **Build Together**: Collaboration multiplies the value for everyone

By building a shared library of instruction sets, the government technology community can:
- Reduce duplicated effort across agencies
- Accelerate adoption of SpecOps methodology
- Preserve knowledge about legacy systems
- Lower barriers to modernization
- Create a lasting resource for future projects

**The instruction sets you create today will help other agencies tomorrow. The instruction sets others create will help you today.**

This is how we build a sustainable approach to legacy modernization across government—not by each agency solving the same problems in isolation, but by sharing knowledge and building together.

---

## Getting Involved

**To use existing instruction sets**:
- Browse the catalog at [repository link TBD]
- Download and customize for your needs
- Provide feedback on effectiveness
- Report issues or suggest improvements

**To contribute new instruction sets**:
- Follow the contribution guidelines
- Submit via pull request
- Participate in community review
- Help maintain and improve over time

**To help build the community**:
- Share your SpecOps experiences
- Present at conferences or user groups
- Write blog posts about your learnings
- Mentor other agencies starting SpecOps projects

Together, we can make legacy modernization more effective, efficient, and sustainable for everyone.