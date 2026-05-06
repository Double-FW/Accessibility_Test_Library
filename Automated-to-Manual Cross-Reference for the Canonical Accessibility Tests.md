# Automated-to-Manual Cross-Reference for the Canonical Accessibility Tests

## Purpose

This document cross-references the 200 canonical tests against the repository-visible scope of four automated testing tools:

1. IBM Equal Access Accessibility Checker
2. Alfa by Siteimprove
3. QualWeb
4. AccessLint

The document is designed for LLM retrieval, policy reasoning, audit planning, and human QA orchestration.

## Source boundary

This document uses only information available from the repository and project pages referenced in the prompt. IBM Equal Access describes its `accessibility-checker-engine` as containing accessibility rules, help, and an evaluation engine, and states that its rules are harmonized with open ACT Rules and provided in rulesets including WCAG 2.2, 2.1, and 2.0 A/AA.

Alfa describes itself as an open, standards-based accessibility conformance testing engine implemented on top of the ACT Rules Format, and its companion `alfa-act-r` repository states that it runs Alfa against official ACT Rules and WCAG test cases and produces both automated and assisted implementation reports.

QualWeb states that its core performs automatic accessibility evaluations and contains three evaluation modules: `@qualweb/act-rules`, `@qualweb/wcag-techniques`, and `@qualweb/best-practices`. Its repository also exposes a rule mapping table from QualWeb rule IDs to ACT Rule IDs and names.

AccessLint states that `@accesslint/core` is a pure accessibility rule engine with zero browser dependencies, covers WCAG 2.2 Level A and AA with best-practice rules included, and exposes bundled rules that can be configured programmatically. Its Storybook addon states that stories are audited automatically after render using the same core engine.

## Interpretation method

The matrix below is an analytical cross-reference, not a claim of exact one-to-one rule identity for every test. Where a repository page clearly exposes direct automated rule coverage, the test is marked `D`. Where repository-visible scope strongly suggests only partial support, such as presence checking without semantic quality checking, the test is marked `P`. Where the repository-visible scope does not evidence reliable automation for the behaviour, the test is marked `N`.

The test names below are preserved verbatim from the canonical 200-test suite.

Legend for coverage columns:

- `D` = direct automated coverage is likely from the repository-visible rule engine or rule modules.
- `P` = partial or complementary automated coverage is likely; automation can usually verify presence, structure, state exposure, or static conformance, but not content quality, task suitability, or full behavioural UX.
- `N` = no reliable automated coverage is evidenced from the repository-visible scope; manual evaluation should be treated as primary.

Legend for duplication flag:

- `HIGH` = strong overlap is likely across three or four automated tools.
- `MED` = overlap is likely across two tools, or one direct tool plus multiple partial tools.
- `LOW` = limited overlap; manual work is still important.
- `NONE` = primarily manual territory.

## Pattern-level recommendation summary

The repository-visible evidence shows that IBM Equal Access, Alfa, and QualWeb are strongest where tests can be expressed as DOM, ARIA, ACT, WCAG, contrast, static structure, and rule-based conformance checks. QualWeb explicitly separates ACT Rules, WCAG techniques, and best-practice modules, while Alfa explicitly builds on ACT Rules and IBM explicitly harmonizes with ACT Rules in addition to its own rulesets. AccessLint is especially useful as a lightweight CI-facing WCAG 2.2 A/AA and best-practice engine, but the repository-visible material is less explicit about deep pattern-specific assisted flows than the first three tools.

The practical consequence is:

- Use **all four automated tools together** for high-overlap static checks such as page title presence, language declaration, accessible name presence, form label presence, many ARIA/state validity checks, contrast, decorative-image suppression, table headers/captions, and some bypass/focus-visible rules.
- Use **IBM + Alfa + QualWeb** as the stronger automated core for component semantics, ACT-aligned rules, ARIA relationships, and rule-heavy structural checks.
- Use **manual testing as the primary method** whenever the test asks whether the text is the *right* text, whether the label is *helpful*, whether an error message is *good enough to recover*, whether a panel or dialog creates the *right user experience*, whether motion is *actually tolerable*, or whether a route change, timeout, or dynamic update preserves *orientation and workflow*.

### Recommended automated + manual combinations by UX pattern

| UX pattern family | Recommended combination |
|---|---|
| Alt text and non-text content | IBM + Alfa + QualWeb + AccessLint for presence, accessible name exposure, decorative suppression, and some media-alternative checks; manual for semantic correctness, salience, sufficiency, and whether the alternative matches the user task. |
| Form labels, names, instructions, and errors | IBM + Alfa + QualWeb + AccessLint for label/name presence, visible-label-in-name style checks, autocomplete validity, required state exposure, and some error association; manual for whether the wording is the right wording, whether instructions are useful, and whether recovery guidance is genuinely actionable. |
| Page titles, language, landmarks, headings, and structural semantics | IBM + Alfa + QualWeb + AccessLint for static presence and validity; manual for uniqueness, quality, narrative appropriateness, and user orientation across journeys. |
| Dialogs, overlays, info panels, tabs, accordions, mega menus, and disclosure patterns | IBM + Alfa + QualWeb for ARIA roles, state exposure, hidden-state handling, and some relationship checks; manual as primary for focus lifecycle, close behaviour, background inertness, escape routes, and interaction predictability. AccessLint is useful in CI for the static subset but should not be treated as sufficient on its own. |
| Carousels, pockets, load more, comments, ratings, cards, promos, and other rich components | Automation for the structural subset only; manual should lead because these patterns depend heavily on sequencing, reveal logic, user control, and meaning quality. |
| Tables and grids | IBM + Alfa + QualWeb + AccessLint for table-vs-layout checks, caption/header presence, scope, and some keyboard-scroll checks; manual for comprehension, scrolling affordance, responsive usability, and whether tabular presentation is actually the right presentation. |
| Media, motion, autoplay, and notification behaviour | Automation can catch some autoplay, control-presence, and caption/alternative conditions, especially in IBM, Alfa, and QualWeb; manual is primary for pause/stop experience, interruption management, real-world perceptibility, and non-disruptive behaviour. |
| Routing, SPA behaviour, timeouts, assistance, and contextual help | Manual is primary. Automation can sometimes verify title updates, skip mechanisms, or static affordances, but route-change announcements, timeouts, progressive help, and workflow continuity require manual flow testing. |

## A. Perception, presentation, and sensory independence

| ID | Canonical test name | IBM Equal Access | Alfa | QualWeb | AccessLint | Automated duplication flag | Manual complement |
|---:|---|:---:|:---:|:---:|:---:|:---:|---|
| 1 | Information Not Conveyed by Colour Alone | D | D | D | P | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 2 | Error States Not Conveyed by Colour Alone | D | D | D | P | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 3 | Required States Not Conveyed by Colour Alone | D | D | D | P | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 4 | Selection State Not Conveyed by Colour Alone | D | D | D | P | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 5 | Focus State Not Conveyed by Colour Alone | D | D | D | P | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 6 | Link Identification Not Conveyed by Colour Alone | D | D | D | P | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 7 | Data Series Not Differentiated Only by Colour | P | P | P | P | LOW | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 8 | Text Contrast Minimum | D | D | D | D | HIGH | Manual confirms content quality, UX suitability, and cross-state behaviour |
| 9 | Large Text Contrast Minimum | D | D | D | D | HIGH | Manual confirms content quality, UX suitability, and cross-state behaviour |
| 10 | Focus Indicator Contrast | D | D | D | D | HIGH | Manual confirms content quality, UX suitability, and cross-state behaviour |
| 11 | Control Boundary Contrast | D | D | D | P | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 12 | Placeholder Contrast Adequacy | D | D | D | P | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 13 | Legibility Under Blur or Reduced Clarity | P | P | P | P | LOW | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 14 | Text Resizes to 200 Percent | D | D | D | D | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 15 | Text Resizes Beyond 200 Percent Where Supported | P | P | P | P | LOW | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 16 | Layout Reflows Without Horizontal Dependency | D | D | D | D | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 17 | No Text Clipping on Resize | D | D | D | D | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 18 | No Functional Loss on Resize | D | D | D | D | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 19 | Text Spacing Override Support | D | D | D | D | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 20 | Zoom Capability Preserved | D | D | D | D | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 21 | Content Usable Under Magnification | P | P | P | P | LOW | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 22 | Motion Respects Reduced Motion Preference | P | P | P | P | LOW | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 23 | Auto-Moving Content Can Be Paused | D | D | D | P | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 24 | Auto-Moving Content Can Be Stopped or Hidden | D | D | D | P | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 25 | Decorative Animation Time-Limited | P | P | P | P | LOW | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 26 | Flashing Content Frequency Safety | P | P | P | P | LOW | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 27 | Flickering Content Warning and Alternative | P | P | P | P | LOW | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 28 | Autoplay Audio Control | D | D | D | P | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 29 | Autoplay Video Control | D | D | D | P | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 30 | Media Does Not Mask Assistive Technology Audio | P | P | P | P | LOW | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 31 | Separate Audio Streams Adjustable | P | P | P | P | LOW | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 32 | Notification Sound Supplemented by Another Modality | P | P | P | P | LOW | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 33 | Decorative Images Ignored by Assistive Technology | D | D | D | P | HIGH | Manual confirms content quality, UX suitability, and cross-state behaviour |
| 34 | Informative Images Have Equivalent Text | D | D | D | D | HIGH | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 35 | Functional Images Describe Action | P | P | P | P | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 36 | Complex Visuals Have Summary | P | P | P | P | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 37 | Images of Text Avoided | D | D | D | P | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 38 | Background Images with Meaning Have Equivalent Content | P | P | P | P | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 39 | Visible Rating or Graphic Indicators Have Text Equivalent | D | D | D | P | HIGH | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 40 | Supplementary Visual Cues Do Not Replace Meaningful Text | P | P | P | P | LOW | Manual confirms real user perceptibility, control usability, and behavioural safety |

## B. Structure, semantics, and document relationships

| ID | Canonical test name | IBM Equal Access | Alfa | QualWeb | AccessLint | Automated duplication flag | Manual complement |
|---:|---|:---:|:---:|:---:|:---:|:---:|---|
| 41 | Primary Page Language Declared | D | D | D | D | HIGH | Manual confirms structural meaning, orientation, and navigation outcome |
| 42 | Inline Language Changes Marked | D | D | D | D | HIGH | Manual confirms structural meaning, orientation, and navigation outcome |
| 43 | Language Direction Specified When Needed | P | P | P | P | LOW | Manual confirms structural meaning, orientation, and navigation outcome |
| 44 | Page Title Present | D | D | D | D | HIGH | Manual confirms structural meaning, orientation, and navigation outcome |
| 45 | Page Title Describes Primary Content | P | P | P | P | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 46 | Page Title Is Unique Within Context | P | P | P | P | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 47 | SPA Title Updates on Route Change | P | P | P | P | LOW | Manual confirms structural meaning, orientation, and navigation outcome |
| 48 | One Main Landmark Per Page | D | D | D | D | HIGH | Manual confirms structural meaning, orientation, and navigation outcome |
| 49 | Major Regions Use Appropriate Landmarks | D | D | D | P | HIGH | Manual confirms structural meaning, orientation, and navigation outcome |
| 50 | Landmark Labels Distinguish Similar Regions | P | P | P | P | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 51 | Content Belongs to Defined Regions | P | P | P | P | LOW | Manual confirms structural meaning, orientation, and navigation outcome |
| 52 | Skip Link or Equivalent Bypass Present | D | D | D | D | HIGH | Manual confirms structural meaning, orientation, and navigation outcome |
| 53 | Skip Link Focuses Main Content Reliably | P | P | P | P | LOW | Manual confirms structural meaning, orientation, and navigation outcome |
| 54 | Heading Structure Present | D | D | D | D | HIGH | Manual confirms structural meaning, orientation, and navigation outcome |
| 55 | One Primary Heading Per Page Context | P | P | P | P | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 56 | Heading Levels Follow Logical Hierarchy | D | D | D | D | HIGH | Manual confirms structural meaning, orientation, and navigation outcome |
| 57 | Heading Text Is Descriptive | P | P | P | P | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 58 | Visual Headings Match Semantic Headings | P | P | P | P | LOW | Manual confirms structural meaning, orientation, and navigation outcome |
| 59 | Headings Are Visually Distinguishable | P | P | P | P | LOW | Manual confirms structural meaning, orientation, and navigation outcome |
| 60 | Source Order Matches Intended Reading Order | D | D | D | P | HIGH | Manual confirms structural meaning, orientation, and navigation outcome |
| 61 | Tab Order Aligns With Logical Structure | D | D | D | P | HIGH | Manual confirms structural meaning, orientation, and navigation outcome |
| 62 | CSS Reordering Does Not Break Meaning | P | P | P | P | LOW | Manual confirms structural meaning, orientation, and navigation outcome |
| 63 | Related Thematic Items Use List Semantics | P | P | P | P | LOW | Manual confirms structural meaning, orientation, and navigation outcome |
| 64 | Arbitrary Layout Containers Avoid False Semantics | P | P | P | P | LOW | Manual confirms structural meaning, orientation, and navigation outcome |
| 65 | Tables Used Only for Tabular Data | D | D | D | D | HIGH | Manual confirms structural meaning, orientation, and navigation outcome |
| 66 | Data Tables Include Header Cells | D | D | D | D | HIGH | Manual confirms structural meaning, orientation, and navigation outcome |
| 67 | Data Table Header Scope Defined | D | D | D | D | HIGH | Manual confirms structural meaning, orientation, and navigation outcome |
| 68 | Data Tables Include Caption | D | D | D | D | HIGH | Manual confirms structural meaning, orientation, and navigation outcome |
| 69 | Table Remains Structurally Intact on Small Screens | P | P | P | P | LOW | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 70 | Scrollable Table Container Is Accessible | D | D | D | P | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |

## C. Naming, labelling, and descriptive clarity

| ID | Canonical test name | IBM Equal Access | Alfa | QualWeb | AccessLint | Automated duplication flag | Manual complement |
|---:|---|:---:|:---:|:---:|:---:|:---:|---|
| 71 | Interactive Elements Have Accessible Names | D | D | D | D | HIGH | Manual confirms content quality, UX suitability, and cross-state behaviour |
| 72 | Visible Labels Exist for Form Inputs | P | P | P | P | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 73 | Accessible Name Matches Visible Label | D | D | D | D | HIGH | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 74 | Label Is Near the Control It Describes | P | P | P | P | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 75 | Label Remains Available During Input | P | P | P | P | LOW | Manual confirms structural meaning, orientation, and navigation outcome |
| 76 | Placeholder Does Not Replace Label | D | D | D | D | HIGH | Manual confirms content quality, UX suitability, and cross-state behaviour |
| 77 | Title Attribute Not Used as Primary Label | D | D | D | D | HIGH | Manual confirms content quality, UX suitability, and cross-state behaviour |
| 78 | Instructions Associated With Relevant Field | P | P | P | P | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 79 | Error Messages Associated With Relevant Field | D | D | D | P | HIGH | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 80 | Group Labels for Related Controls | D | D | D | P | HIGH | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 81 | Control Text Describes Purpose | P | P | P | P | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 82 | Icon-Only Controls Have Equivalent Text | D | D | D | P | HIGH | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 83 | Supplementary Help Does Not Duplicate Primary Name | P | P | P | P | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 84 | External Navigation Warns of Context Change | D | D | D | P | HIGH | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 85 | New Window or New Tab Behaviour Disclosed | D | D | D | P | HIGH | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 86 | Breadcrumb Current Item Labelled Correctly | D | D | D | P | HIGH | Manual confirms content quality, UX suitability, and cross-state behaviour |
| 87 | Current Navigation Item Exposed | D | D | D | P | HIGH | Manual confirms content quality, UX suitability, and cross-state behaviour |
| 88 | Metadata Values Clarified Non-Visually | P | P | P | P | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 89 | Breakout and Complementary Sections Uniquely Labelled | P | P | P | P | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 90 | Comments, Panels, and Supplemental Regions Clearly Named | P | P | P | P | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |

## D. Keyboard, focus, and input modality

| ID | Canonical test name | IBM Equal Access | Alfa | QualWeb | AccessLint | Automated duplication flag | Manual complement |
|---:|---|:---:|:---:|:---:|:---:|:---:|---|
| 91 | All Interactive Elements Reachable by Keyboard | D | D | D | D | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 92 | All Interactive Elements Operable by Keyboard | D | D | D | D | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 93 | Standard Keyboard Activation Preserved | P | P | P | P | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 94 | No Keyboard Trap | D | D | D | D | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 95 | Focus Indicator Always Visible | D | D | D | D | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 96 | Focus Indicator Not Suppressed Without Equivalent | D | D | D | P | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 97 | Focus Order Logical Through Forms | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 98 | Focus Order Logical Through Navigation | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 99 | Focus Does Not Move Unexpectedly During Input | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 100 | Focus Moves to New Context on Open | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 101 | Focus Returns on Close | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 102 | Programmatic Focus Uses Appropriate Targets | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 103 | Hidden Focusable Elements Revealed on Focus | D | D | D | P | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 104 | Positive Tabindex Avoided | D | D | D | D | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 105 | Tabindex Zero Used Only on Intended Interactive Targets | D | D | D | P | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 106 | Tabindex Minus One Used for Programmatic Focus Only | D | D | D | P | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 107 | Alternative Input Method Support | P | P | P | N | LOW | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 108 | Gesture Functions Have Non-Gesture Alternatives | P | P | P | N | LOW | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 109 | Pointer Precision Not Required for Basic Tasks | P | P | P | N | LOW | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 110 | Target Size Meets Minimum Usability Threshold | P | P | P | N | LOW | Manual confirms real user perceptibility, control usability, and behavioural safety |

## E. Forms, input, and validation

| ID | Canonical test name | IBM Equal Access | Alfa | QualWeb | AccessLint | Automated duplication flag | Manual complement |
|---:|---|:---:|:---:|:---:|:---:|:---:|---|
| 111 | Explicit Submit Control Present | D | D | D | P | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 112 | Submission Occurs Only on Explicit Action | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 113 | Required Fields Indicated Programmatically | D | D | D | D | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 114 | Required Fields Indicated Visually | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 115 | Optional Fields Marked Where Pattern Requires | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 116 | Input Format Expectations Communicated | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 117 | Appropriate Input Type Used | D | D | D | D | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 118 | Autocomplete Used for Personal Data Where Appropriate | D | D | D | D | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 119 | Related Inputs Grouped Semantically | D | D | D | P | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 120 | Radio Groups Operate as One Logical Question | D | D | D | P | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 121 | Checkbox Sets Grouped Where They Share a Question | D | D | D | P | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 122 | Error Messages Shown When Submission Fails | D | D | D | D | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 123 | Error Messages Are Announced to Assistive Technology | D | D | D | D | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 124 | Error Message Identifies the Relevant Field | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 125 | Error Message Explains the Problem | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 126 | Error Message Tells User How to Fix It | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 127 | Error Summary Provided for Multiple Errors | P | P | P | P | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 128 | Error Summary Supports Navigation to Fields | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 129 | User Input Preserved After Validation Failure | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 130 | Validation Does Not Interrupt Every Keystroke Inappropriately | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 131 | Error Cues Persist Long Enough to Be Used | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 132 | Reset Buttons Avoided or Safe | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 133 | Form Completion Possible by Keyboard Only | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 134 | Password and Complex Input Assistance Available | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 135 | Submit Controls Not Inaccessibly Disabled | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |

## F. Links, navigation systems, and routing

| ID | Canonical test name | IBM Equal Access | Alfa | QualWeb | AccessLint | Automated duplication flag | Manual complement |
|---:|---|:---:|:---:|:---:|:---:|:---:|---|
| 136 | Link Purpose Understandable in Isolation | D | D | D | D | HIGH | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 137 | Repeated Link Text Distinguishable Where Destinations Differ | D | D | D | D | HIGH | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 138 | Adjacent Duplicate Links Consolidated | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 139 | External Link Warning Included | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 140 | Download or Alternate Format Links Identified | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 141 | Breadcrumbs Structured as Navigation List | D | D | D | P | HIGH | Manual confirms structural meaning, orientation, and navigation outcome |
| 142 | Breadcrumb Current Page Is Not an Active Link | P | P | P | N | LOW | Manual confirms structural meaning, orientation, and navigation outcome |
| 143 | Navigation Menus Use Correct Structural Semantics | D | D | D | D | HIGH | Manual confirms structural meaning, orientation, and navigation outcome |
| 144 | Current Navigation State Programmatically Exposed | D | D | D | P | HIGH | Manual confirms structural meaning, orientation, and navigation outcome |
| 145 | Search Region Identifiable | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 146 | Search Suggestions Announced Accessibly | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 147 | Share and Auxiliary Tool Clarity | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 148 | SPA Route Changes Update Focus Position | P | P | P | N | LOW | Manual confirms structural meaning, orientation, and navigation outcome |
| 149 | SPA Route Changes Update History | P | P | P | N | LOW | Manual confirms structural meaning, orientation, and navigation outcome |
| 150 | Route Change Loading State Communicated | P | P | P | N | LOW | Manual confirms structural meaning, orientation, and navigation outcome |

## G. Dynamic content, notifications, and state change

| ID | Canonical test name | IBM Equal Access | Alfa | QualWeb | AccessLint | Automated duplication flag | Manual complement |
|---:|---|:---:|:---:|:---:|:---:|:---:|---|
| 151 | Status Messages Announced Without Forced Focus Change | D | D | D | D | HIGH | Manual confirms content quality, UX suitability, and cross-state behaviour |
| 152 | Critical Alerts Perceivable in Multiple Modalities | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 153 | Notifications Not Overbearing | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 154 | Standard OS or Platform Notifications Used When Appropriate | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 155 | Dynamic Content Discoverable After Update | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 156 | Focus Not Stolen by Non-Critical Updates | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 157 | State Changes Reflected Programmatically | D | D | D | D | HIGH | Manual confirms content quality, UX suitability, and cross-state behaviour |
| 158 | State Change Announced When It Matters | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 159 | Live Regions Used Appropriately | D | D | D | P | HIGH | Manual confirms content quality, UX suitability, and cross-state behaviour |
| 160 | Update Timing Allows Perception | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |

## H. Components: disclosure, overlays, and grouped interaction

| ID | Canonical test name | IBM Equal Access | Alfa | QualWeb | AccessLint | Automated duplication flag | Manual complement |
|---:|---|:---:|:---:|:---:|:---:|:---:|---|
| 161 | Disclosure Controls Expose Expanded State | D | D | D | D | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 162 | Disclosure Controls and Content Linked | D | D | D | P | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 163 | Collapsed Disclosure Content Removed Accessibly | D | D | D | P | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 164 | Revealed Content Follows Control Logically | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 165 | Accordion Items Use Heading + Button Pattern | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 166 | Single-Select Accordions Enforce One Open Item | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 167 | Tabs Use Correct Roles When Enhanced | D | D | D | D | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 168 | Tabs Preserve Non-JavaScript Access | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 169 | Only Active Tab Panel Exposed | D | D | D | P | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 170 | Information Panels Open and Close Predictably | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 171 | Information Panels Not Used for Essential-Only Content | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 172 | Modal Dialog Announces Identity and Modality | D | D | D | D | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 173 | Modal Dialog Blocks Background Interaction | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 174 | Modal Dialog Has Accessible Close Method | D | D | D | P | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 175 | Modal Dialog Content Fits or Scrolls | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 176 | Action Dialog Uses Buttons vs Links Appropriately | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 177 | Mega Menu Trigger Uses Button Semantics | D | D | D | P | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 178 | Mega Menu Closes on Escape, Blur, or Outside Click | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 179 | Carousel Is Entirely User Driven | P | P | P | N | LOW | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 180 | Carousel Hidden or Faint Items Not Presented as Fully Available | P | P | P | N | LOW | Manual confirms real user perceptibility, control usability, and behavioural safety |

## I. Media, promos, cards, comments, and rich content patterns

| ID | Canonical test name | IBM Equal Access | Alfa | QualWeb | AccessLint | Automated duplication flag | Manual complement |
|---:|---|:---:|:---:|:---:|:---:|:---:|---|
| 181 | Native Media Controls or Accessible Equivalent Present | D | D | D | D | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 182 | Media Does Not Autoplay Unexpectedly | D | D | D | D | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 183 | Captions Available for Spoken Video | D | D | D | D | HIGH | Manual confirms real user perceptibility, control usability, and behavioural safety |
| 184 | Audio Description or Equivalent for Essential Visual Information | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 185 | Promo Has One Clear Primary Action | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 186 | Promo Headline Consistent With Destination | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 187 | Promo Media Indicators Explained Non-Visually | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 188 | Card Collections Use List Structure | D | D | D | P | HIGH | Manual confirms content quality, UX suitability, and cross-state behaviour |
| 189 | Card Headline Comes First in Source Order | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 190 | Card Expandable Regions Follow Toggle State | D | D | D | P | HIGH | Manual confirms content quality, UX suitability, and cross-state behaviour |
| 191 | Comment Stream Uses Nested Structure for Replies | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 192 | Comment Submission Feedback Accessible | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 193 | Comment Controls Clearly Labelled | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 194 | Character Limits Communicated During Comment Entry | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 195 | Rating Displays Express Value in Text | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 196 | Interactive Ratings Use Semantic Form Controls | D | D | D | D | HIGH | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |

## J. Time, persistence, and system behaviour

| ID | Canonical test name | IBM Equal Access | Alfa | QualWeb | AccessLint | Automated duplication flag | Manual complement |
|---:|---|:---:|:---:|:---:|:---:|:---:|---|
| 197 | Time Limits Can Be Extended, Disabled, or Adjusted | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 198 | Timeout Warning Issued Before Expiry | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
| 199 | Timeout Consequences Communicated | P | P | P | N | LOW | Manual confirms semantic correctness, wording quality, and task-level appropriateness |
| 200 | Unexpected Context Changes Prevented | P | P | P | N | LOW | Manual confirms full interaction flow, focus lifecycle, and recovery behaviour |
