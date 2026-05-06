# Canonical Test Inventory: token dependencies and bi-directional component mapping

Source basis: the 200-test canonical inventory uploaded in this conversation. Component and token dependencies below are an implementation inference from each test requirement and supported user behaviour.

## 1) Test -> impacted components + token dependencies

| ID | Canonical test | Domain | Impacted components / patterns | Design token dependencies |
|---:|---|---|---|---|
| 1 | Information Not Conveyed by Colour Alone | Perception, presentation, and sensory independence | Status badge; Alert; Validation state; Chart; Filter chip; Tabs; Navigation item | color.foreground; color.background; color.state.*; icon.semantic; content.statusText |
| 2 | Error States Not Conveyed by Colour Alone | Perception, presentation, and sensory independence | Form field; Error summary; Inline validation; Alert | color.error.*; icon.error; content.error; typography.emphasis |
| 3 | Required States Not Conveyed by Colour Alone | Perception, presentation, and sensory independence | Input; Select; Checkbox; Radio; Group label | content.requiredIndicator; color.state.required; typography.label; semantic.required |
| 4 | Selection State Not Conveyed by Colour Alone | Perception, presentation, and sensory independence | Tabs; Segmented control; Listbox; Menu; Card selector; Pagination | color.state.selected; icon.selected; border.selected; semantic.selected |
| 5 | Focus State Not Conveyed by Colour Alone | Perception, presentation, and sensory independence | All interactive components | focus.visible; focus.ring.*; outline.*; border.focus |
| 6 | Link Identification Not Conveyed by Colour Alone | Perception, presentation, and sensory independence | Inline link; Navigation link; Card link | color.link.*; typography.linkDecoration; border.linkUnderline |
| 7 | Data Series Not Differentiated Only by Colour | Perception, presentation, and sensory independence | Chart; Graph; Legend | color.chart.*; pattern.chart.*; content.seriesLabel; shape.series |
| 8 | Text Contrast Minimum | Perception, presentation, and sensory independence | Body text; Label; Button text; Link text; Alert text | color.foreground; color.background; color.state.* |
| 9 | Large Text Contrast Minimum | Perception, presentation, and sensory independence | Heading; Hero text; Large button label | color.foreground; color.background; typography.scale.* |
| 10 | Focus Indicator Contrast | Perception, presentation, and sensory independence | All interactive components | focus.ring.*; color.focus; outline.width |
| 11 | Control Boundary Contrast | Perception, presentation, and sensory independence | Button; Input; Select; Checkbox; Radio; Card action | border.*; color.border.*; color.background |
| 12 | Placeholder Contrast Adequacy | Perception, presentation, and sensory independence | Input; Textarea; Search field | color.placeholder; typography.placeholder |
| 13 | Legibility Under Blur or Reduced Clarity | Perception, presentation, and sensory independence | Body text; Heading; Data table; Form labels | typography.scale.*; lineHeight.*; color.foreground; fontWeight.* |
| 14 | Text Resizes to 200 Percent | Perception, presentation, and sensory independence | All text-bearing components; Layout | typography.scale.*; layout.grid; spacing.* |
| 15 | Text Resizes Beyond 200 Percent Where Supported | Perception, presentation, and sensory independence | All text-bearing components; Layout | typography.scale.*; layout.grid; spacing.*; container.maxWidth |
| 16 | Layout Reflows Without Horizontal Dependency | Perception, presentation, and sensory independence | Layout; Article; Form; Navigation; Data display | layout.grid; container.width; spacing.*; breakpoint.* |
| 17 | No Text Clipping on Resize | Perception, presentation, and sensory independence | Button; Input; Tag; Badge; Navigation item; Card | spacing.*; lineHeight.*; component.minHeight |
| 18 | No Functional Loss on Resize | Perception, presentation, and sensory independence | All interactive components; Layout | layout.grid; spacing.*; component.minTarget |
| 19 | Text Spacing Override Support | Perception, presentation, and sensory independence | Article; Long-form text; Form help; Error text | typography.letterSpacing; typography.wordSpacing; typography.lineHeight; spacing.paragraph |
| 20 | Zoom Capability Preserved | Perception, presentation, and sensory independence | App shell; Viewport; Layout | viewport.meta; layout.scalePolicy |
| 21 | Content Usable Under Magnification | Perception, presentation, and sensory independence | All components; Layout; Navigation | layout.grid; spacing.*; focus.visible; sticky.offset |
| 22 | Motion Respects Reduced Motion Preference | Perception, presentation, and sensory independence | Carousel; Modal; Toast; Accordion; Tooltip; Transitions | motion.duration.*; motion.easing.*; motion.reduced.* |
| 23 | Auto-Moving Content Can Be Paused | Perception, presentation, and sensory independence | Carousel; Marquee; Ticker; Rotator | motion.autoAdvance; controls.pause |
| 24 | Auto-Moving Content Can Be Stopped or Hidden | Perception, presentation, and sensory independence | Carousel; Ticker; Animated banner | motion.autoAdvance; controls.stop; visibility.toggle |
| 25 | Decorative Animation Time-Limited | Perception, presentation, and sensory independence | Decorative animation; Hero motion; Ambient effects | motion.duration.*; motion.loop; motion.reduced.* |
| 26 | Flashing Content Frequency Safety | Perception, presentation, and sensory independence | Animation; Video; Promotional banner | motion.flashRate; media.playbackPolicy |
| 27 | Flickering Content Warning and Alternative | Perception, presentation, and sensory independence | Media player; Promo; Animation panel | content.warning; content.alternative; media.playbackPolicy |
| 28 | Autoplay Audio Control | Perception, presentation, and sensory independence | Audio player; Video player; Promo media | media.autoplay; media.controls; controls.mute |
| 29 | Autoplay Video Control | Perception, presentation, and sensory independence | Video player; Carousel video; Hero media | media.autoplay; media.controls |
| 30 | Media Does Not Mask Assistive Technology Audio | Perception, presentation, and sensory independence | Media player; System audio UI | media.volume; media.ducking; media.audioMix |
| 31 | Separate Audio Streams Adjustable | Perception, presentation, and sensory independence | Media player; Podcast player; Multitrack player | media.volume.*; media.audioTrack.* |
| 32 | Notification Sound Supplemented by Another Modality | Perception, presentation, and sensory independence | Toast; Alert; System notification | sound.notification; haptics.*; color.alert.*; content.alertText |
| 33 | Decorative Images Ignored by Assistive Technology | Perception, presentation, and sensory independence | Image; Icon; Divider illustration; Background media | content.altText; semantic.decorative |
| 34 | Informative Images Have Equivalent Text | Perception, presentation, and sensory independence | Image; Figure; Card media | content.altText; content.caption |
| 35 | Functional Images Describe Action | Perception, presentation, and sensory independence | Image button; Promo media CTA; Iconic control | content.altText; content.actionLabel |
| 36 | Complex Visuals Have Summary | Perception, presentation, and sensory independence | Chart; Diagram; Infographic; Map | content.summary; content.longDescription; data.tableFallback |
| 37 | Images of Text Avoided | Perception, presentation, and sensory independence | Hero banner; Promo; Card; Badge; Navigation logo | content.text; media.imagePolicy; typography.* |
| 38 | Background Images with Meaning Have Equivalent Content | Perception, presentation, and sensory independence | Hero; Promo; Banner; Card | content.body; content.altEquivalent; media.backgroundPolicy |
| 39 | Visible Rating or Graphic Indicators Have Text Equivalent | Perception, presentation, and sensory independence | Rating display; Review summary; Progress indicator | content.valueText; icon.semantic |
| 40 | Supplementary Visual Cues Do Not Replace Meaningful Text | Perception, presentation, and sensory independence | Status badge; Avatar; Icon label; Metadata chip | content.body; content.statusText; icon.semantic |
| 41 | Primary Page Language Declared | Structure, semantics, and document relationships | App shell; Page template; Document root | content.language; document.lang |
| 42 | Inline Language Changes Marked | Structure, semantics, and document relationships | Rich text; Article; Comment; Inline quote | content.language.inline |
| 43 | Language Direction Specified When Needed | Structure, semantics, and document relationships | Rich text; Input; Comment thread; Messaging UI | content.direction; layout.direction |
| 44 | Page Title Present | Structure, semantics, and document relationships | Page template; Route container; SPA shell | content.title |
| 45 | Page Title Describes Primary Content | Structure, semantics, and document relationships | Page template; Route container | content.title; content.pagePurpose |
| 46 | Page Title Is Unique Within Context | Structure, semantics, and document relationships | Page template; Route container; Navigation state | content.title; routing.routeName |
| 47 | SPA Title Updates on Route Change | Structure, semantics, and document relationships | SPA shell; Router; View container | content.title; routing.routeName |
| 48 | One Main Landmark Per Page | Structure, semantics, and document relationships | Page template; Layout shell | layout.landmarks.main |
| 49 | Major Regions Use Appropriate Landmarks | Structure, semantics, and document relationships | Header; Nav; Main; Footer; Aside; Search | layout.landmarks.* |
| 50 | Landmark Labels Distinguish Similar Regions | Structure, semantics, and document relationships | Multiple navs; Asides; complementary regions | content.landmarkLabel |
| 51 | Content Belongs to Defined Regions | Structure, semantics, and document relationships | Page template; Layout shell; Section wrapper | layout.landmarks.*; layout.region |
| 52 | Skip Link or Equivalent Bypass Present | Structure, semantics, and document relationships | Page template; Global nav; App shell | focus.skipLink; layout.landmarks.main |
| 53 | Skip Link Focuses Main Content Reliably | Structure, semantics, and document relationships | Skip link; Main content container | focus.skipLink; focus.programmatic |
| 54 | Heading Structure Present | Structure, semantics, and document relationships | Article; Form; Settings page; Dialog | typography.heading.*; semantic.heading |
| 55 | One Primary Heading Per Page Context | Structure, semantics, and document relationships | Page header; Article; View container | typography.heading.h1; content.pageHeading |
| 56 | Heading Levels Follow Logical Hierarchy | Structure, semantics, and document relationships | Section; Accordion; Dialog; Article | typography.heading.*; semantic.headingLevel |
| 57 | Heading Text Is Descriptive | Structure, semantics, and document relationships | Heading; Section header; Card headline | content.heading |
| 58 | Visual Headings Match Semantic Headings | Structure, semantics, and document relationships | Heading component; Rich text; Section header | typography.heading.*; semantic.heading |
| 59 | Headings Are Visually Distinguishable | Structure, semantics, and document relationships | Heading; Section header | typography.heading.*; color.foreground; spacing.heading |
| 60 | Source Order Matches Intended Reading Order | Structure, semantics, and document relationships | Card; Promo; Layout; Modal; Form | layout.order; semantic.order |
| 61 | Tab Order Aligns With Logical Structure | Structure, semantics, and document relationships | All interactive components; Form; Nav; Modal | focus.order; semantic.order |
| 62 | CSS Reordering Does Not Break Meaning | Structure, semantics, and document relationships | Grid; Card list; Sidebar layout; Form | layout.order; breakpoint.* |
| 63 | Related Thematic Items Use List Semantics | Structure, semantics, and document relationships | Card collection; Nav list; Comments; Search results | semantic.list; spacing.stack |
| 64 | Arbitrary Layout Containers Avoid False Semantics | Structure, semantics, and document relationships | Grid; Columns; Layout wrapper | semantic.layoutContainer |
| 65 | Tables Used Only for Tabular Data | Structure, semantics, and document relationships | Data table; Comparison table | semantic.table |
| 66 | Data Tables Include Header Cells | Structure, semantics, and document relationships | Data table | semantic.table; typography.tableHeader |
| 67 | Data Table Header Scope Defined | Structure, semantics, and document relationships | Data table | semantic.table; content.headerScope |
| 68 | Data Tables Include Caption | Structure, semantics, and document relationships | Data table | content.caption; semantic.table |
| 69 | Table Remains Structurally Intact on Small Screens | Structure, semantics, and document relationships | Responsive table; Comparison table | layout.tableResponsive; breakpoint.* |
| 70 | Scrollable Table Container Is Accessible | Structure, semantics, and document relationships | Scrollable table wrapper | focus.programmatic; content.scrollRegionLabel; layout.overflow |
| 71 | Interactive Elements Have Accessible Names | Naming, labelling, and descriptive clarity | Button; Link; Input; Select; Checkbox; Radio; Toggle; Menu item | content.label; aria.label; semantic.name |
| 72 | Visible Labels Exist for Form Inputs | Naming, labelling, and descriptive clarity | Input; Select; Textarea; Search field | content.label.visible; typography.label |
| 73 | Accessible Name Matches Visible Label | Naming, labelling, and descriptive clarity | Input; Button; Link; Toggle; Menu item | content.label; aria.label |
| 74 | Label Is Near the Control It Describes | Naming, labelling, and descriptive clarity | Form field; Checkbox; Radio group | spacing.form; layout.fieldPairing |
| 75 | Label Remains Available During Input | Naming, labelling, and descriptive clarity | Floating label field; Input; Textarea | content.label.visible; motion.label |
| 76 | Placeholder Does Not Replace Label | Naming, labelling, and descriptive clarity | Input; Search field; Textarea | content.placeholder; content.label.visible |
| 77 | Title Attribute Not Used as Primary Label | Naming, labelling, and descriptive clarity | Any form control; Icon-only control | aria.label; content.label.visible |
| 78 | Instructions Associated With Relevant Field | Naming, labelling, and descriptive clarity | Form field; Password field; Date input | content.helpText; aria.describedby |
| 79 | Error Messages Associated With Relevant Field | Naming, labelling, and descriptive clarity | Form field; Error summary; Inline validation | content.error; aria.describedby; semantic.invalid |
| 80 | Group Labels for Related Controls | Naming, labelling, and descriptive clarity | Fieldset; Radio group; Checkbox group; Address group | content.groupLabel; semantic.group |
| 81 | Control Text Describes Purpose | Naming, labelling, and descriptive clarity | Button; Link; Menu item; CTA | content.actionLabel; content.linkText |
| 82 | Icon-Only Controls Have Equivalent Text | Naming, labelling, and descriptive clarity | Icon button; Toolbar action; Overflow menu trigger | content.actionLabel; icon.semantic; aria.label |
| 83 | Supplementary Help Does Not Duplicate Primary Name | Naming, labelling, and descriptive clarity | Tooltip; Hint text; Help panel | content.helpText; aria.describedby |
| 84 | External Navigation Warns of Context Change | Naming, labelling, and descriptive clarity | External link; Nav item; CTA | content.externalWarning; icon.external |
| 85 | New Window or New Tab Behaviour Disclosed | Naming, labelling, and descriptive clarity | Link; CTA; Download link | content.newContextWarning; icon.newWindow |
| 86 | Breadcrumb Current Item Labelled Correctly | Naming, labelling, and descriptive clarity | Breadcrumb | semantic.current; content.currentLabel |
| 87 | Current Navigation Item Exposed | Naming, labelling, and descriptive clarity | Tabs; Menu; Breadcrumb; Filter chips; Pagination | semantic.current; semantic.selected |
| 88 | Metadata Values Clarified Non-Visually | Naming, labelling, and descriptive clarity | Date chip; Duration; Source metadata; Stats | content.valueText; content.ariaLabel |
| 89 | Breakout and Complementary Sections Uniquely Labelled | Naming, labelling, and descriptive clarity | Aside; Related links; Supplemental panel | content.landmarkLabel |
| 90 | Comments, Panels, and Supplemental Regions Clearly Named | Naming, labelling, and descriptive clarity | Comments region; Drawer; Supplemental panel; Share tools | content.regionLabel; aria.label |
| 91 | All Interactive Elements Reachable by Keyboard | Keyboard, focus, and input modality | All interactive components | focus.order; semantic.interactive |
| 92 | All Interactive Elements Operable by Keyboard | Keyboard, focus, and input modality | All interactive components | semantic.activation; keyboard.binding |
| 93 | Standard Keyboard Activation Preserved | Keyboard, focus, and input modality | Button; Link; Checkbox; Radio; Menu item | keyboard.binding; semantic.interactive |
| 94 | No Keyboard Trap | Keyboard, focus, and input modality | Modal; Menu; Editor; Media player; Carousel | focus.trap; focus.escape |
| 95 | Focus Indicator Always Visible | Keyboard, focus, and input modality | All interactive components | focus.visible; focus.ring.* |
| 96 | Focus Indicator Not Suppressed Without Equivalent | Keyboard, focus, and input modality | All interactive components | focus.visible; focus.ring.* |
| 97 | Focus Order Logical Through Forms | Keyboard, focus, and input modality | Form; Wizard; Checkout | focus.order; layout.formFlow |
| 98 | Focus Order Logical Through Navigation | Keyboard, focus, and input modality | Header nav; Sidebar nav; Breadcrumb; Pagination | focus.order; layout.navigationFlow |
| 99 | Focus Does Not Move Unexpectedly During Input | Keyboard, focus, and input modality | Form; Combobox; OTP input | focus.programmatic; state.changePolicy |
| 100 | Focus Moves to New Context on Open | Keyboard, focus, and input modality | Modal; Dialog; Drawer; Popover | focus.programmatic; focus.trap |
| 101 | Focus Returns on Close | Keyboard, focus, and input modality | Modal; Dialog; Drawer; Popover; Info panel | focus.returnTarget |
| 102 | Programmatic Focus Uses Appropriate Targets | Keyboard, focus, and input modality | Modal; Alert; Error summary; SPA route | focus.programmatic; semantic.target |
| 103 | Hidden Focusable Elements Revealed on Focus | Keyboard, focus, and input modality | Skip link; Off-canvas control; Hidden utility link | focus.visible; visibility.onFocus |
| 104 | Positive Tabindex Avoided | Keyboard, focus, and input modality | All interactive components | focus.order |
| 105 | Tabindex Zero Used Only on Intended Interactive Targets | Keyboard, focus, and input modality | Custom controls; Scroll regions; Panels | focus.order; semantic.interactive |
| 106 | Tabindex Minus One Used for Programmatic Focus Only | Keyboard, focus, and input modality | Main target; Error summary; Dialog heading | focus.programmatic |
| 107 | Alternative Input Method Support | Keyboard, focus, and input modality | All interactive components | semantic.interactive; keyboard.binding; target.size |
| 108 | Gesture Functions Have Non-Gesture Alternatives | Keyboard, focus, and input modality | Carousel; Slider; Map; Reorder list; Drag/drop | gesture.alternative; keyboard.binding |
| 109 | Pointer Precision Not Required for Basic Tasks | Keyboard, focus, and input modality | Small icon buttons; Map controls; Dense menus | target.size; spacing.hitArea |
| 110 | Target Size Meets Minimum Usability Threshold | Keyboard, focus, and input modality | Button; Link; Chip; Pagination; Toggle | target.size; spacing.hitArea |
| 111 | Explicit Submit Control Present | Forms, input, and validation | Form; Comment form; Search form | content.actionLabel; semantic.submit |
| 112 | Submission Occurs Only on Explicit Action | Forms, input, and validation | Form; Select; Filter bar | state.changePolicy; semantic.submit |
| 113 | Required Fields Indicated Programmatically | Forms, input, and validation | Input; Select; Textarea; Checkbox group | semantic.required; aria.required |
| 114 | Required Fields Indicated Visually | Forms, input, and validation | Input; Select; Textarea; Checkbox group | content.requiredIndicator; color.state.required |
| 115 | Optional Fields Marked Where Pattern Requires | Forms, input, and validation | Form field; Optional metadata | content.optionalIndicator |
| 116 | Input Format Expectations Communicated | Forms, input, and validation | Date input; Phone input; Password field; OTP | content.helpText; content.formatHint |
| 117 | Appropriate Input Type Used | Forms, input, and validation | Email input; Tel input; Number input; Date input | semantic.inputType; input.mode |
| 118 | Autocomplete Used for Personal Data Where Appropriate | Forms, input, and validation | Address form; Payment form; Profile form | semantic.autocomplete |
| 119 | Related Inputs Grouped Semantically | Forms, input, and validation | Fieldset; Address group; Payment group | semantic.group; content.groupLabel |
| 120 | Radio Groups Operate as One Logical Question | Forms, input, and validation | Radio group | semantic.group; content.groupLabel |
| 121 | Checkbox Sets Grouped Where They Share a Question | Forms, input, and validation | Checkbox group | semantic.group; content.groupLabel |
| 122 | Error Messages Shown When Submission Fails | Forms, input, and validation | Form; Comment form; Checkout | content.error; color.error.* |
| 123 | Error Messages Are Announced to Assistive Technology | Forms, input, and validation | Form; Error summary; Inline validation | content.error; aria.live; aria.describedby |
| 124 | Error Message Identifies the Relevant Field | Forms, input, and validation | Form field; Error summary | content.error; content.fieldLabel |
| 125 | Error Message Explains the Problem | Forms, input, and validation | Form field; Error summary | content.error |
| 126 | Error Message Tells User How to Fix It | Forms, input, and validation | Form field; Error summary; Password field | content.error; content.helpText |
| 127 | Error Summary Provided for Multiple Errors | Forms, input, and validation | Long form; Checkout; Registration | content.errorSummary; focus.programmatic |
| 128 | Error Summary Supports Navigation to Fields | Forms, input, and validation | Error summary | content.errorSummary; focus.programmatic |
| 129 | User Input Preserved After Validation Failure | Forms, input, and validation | Form; Comment form; Checkout | state.formPersistence |
| 130 | Validation Does Not Interrupt Every Keystroke Inappropriately | Forms, input, and validation | Form field; Search field; Password field | state.validationTiming |
| 131 | Error Cues Persist Long Enough to Be Used | Forms, input, and validation | Toast; Inline validation; Error summary | state.messageDuration; content.error |
| 132 | Reset Buttons Avoided or Safe | Forms, input, and validation | Form; Settings form | semantic.reset; content.warning |
| 133 | Form Completion Possible by Keyboard Only | Forms, input, and validation | Entire form journey | focus.order; keyboard.binding |
| 134 | Password and Complex Input Assistance Available | Forms, input, and validation | Password field; OTP; Security question | content.helpText; content.requirements |
| 135 | Submit Controls Not Inaccessibly Disabled | Forms, input, and validation | Submit button; Save button | state.disabledPolicy; color.state.disabled; content.actionHint |
| 136 | Link Purpose Understandable in Isolation | Links, navigation systems, and routing | Inline link; Card link; Footer link; Breadcrumb | content.linkText; aria.label |
| 137 | Repeated Link Text Distinguishable Where Destinations Differ | Links, navigation systems, and routing | Lists of links; Cards; Related links | content.linkText; aria.label |
| 138 | Adjacent Duplicate Links Consolidated | Links, navigation systems, and routing | Card; Teaser; Media promo | semantic.linkGrouping |
| 139 | External Link Warning Included | Links, navigation systems, and routing | External link; Footer link; CTA | content.externalWarning; icon.external |
| 140 | Download or Alternate Format Links Identified | Links, navigation systems, and routing | Download link; PDF link; App store link | content.formatLabel; icon.download |
| 141 | Breadcrumbs Structured as Navigation List | Links, navigation systems, and routing | Breadcrumb | layout.landmarks.nav; semantic.list |
| 142 | Breadcrumb Current Page Is Not an Active Link | Links, navigation systems, and routing | Breadcrumb | semantic.current |
| 143 | Navigation Menus Use Correct Structural Semantics | Links, navigation systems, and routing | Global nav; Sidebar nav; Footer nav; Mega menu | layout.landmarks.nav; semantic.list |
| 144 | Current Navigation State Programmatically Exposed | Links, navigation systems, and routing | Tabs; Menu; Pagination; Breadcrumb; Filter | semantic.current; semantic.selected |
| 145 | Search Region Identifiable | Links, navigation systems, and routing | Search form; Search results header | layout.landmarks.search; content.regionLabel |
| 146 | Search Suggestions Announced Accessibly | Links, navigation systems, and routing | Autocomplete; Search suggest; Typeahead | aria.live; semantic.listbox; content.suggestionText |
| 147 | Share and Auxiliary Tool Clarity | Links, navigation systems, and routing | Share tools; Save; Print; Overflow menu | content.actionLabel; icon.semantic |
| 148 | SPA Route Changes Update Focus Position | Links, navigation systems, and routing | SPA shell; Route container | focus.programmatic; routing.routeName |
| 149 | SPA Route Changes Update History | Links, navigation systems, and routing | SPA shell; Router | routing.history |
| 150 | Route Change Loading State Communicated | Links, navigation systems, and routing | SPA shell; Route loader; Skeleton | state.loading; aria.live; content.loadingText |
| 151 | Status Messages Announced Without Forced Focus Change | Dynamic content, notifications, and state change | Toast; Inline success; Status banner | aria.live; state.messageDuration |
| 152 | Critical Alerts Perceivable in Multiple Modalities | Dynamic content, notifications, and state change | Critical alert; System alert; Confirmation failure | aria.live; color.alert.*; sound.notification; haptics.* |
| 153 | Notifications Not Overbearing | Dynamic content, notifications, and state change | Toast system; Notification center | state.messageFrequency; state.messageDuration |
| 154 | Standard OS or Platform Notifications Used When Appropriate | Dynamic content, notifications, and state change | Native notification bridge; App shell | platform.notification |
| 155 | Dynamic Content Discoverable After Update | Dynamic content, notifications, and state change | Infinite list; Comments; Expand-on-load section | aria.live; focus.programmatic; content.updateLabel |
| 156 | Focus Not Stolen by Non-Critical Updates | Dynamic content, notifications, and state change | Toast; Autosave; Suggestion update | focus.programmatic; state.changePolicy |
| 157 | State Changes Reflected Programmatically | Dynamic content, notifications, and state change | Disclosure; Checkbox; Toggle; Tabs; Tree; Accordion | semantic.expanded; semantic.selected; semantic.checked; semantic.invalid |
| 158 | State Change Announced When It Matters | Dynamic content, notifications, and state change | Form submit; Save state; Toggle; Selection | aria.live; semantic.stateText |
| 159 | Live Regions Used Appropriately | Dynamic content, notifications, and state change | Toast; Status area; Search suggest | aria.live; aria.politeness |
| 160 | Update Timing Allows Perception | Dynamic content, notifications, and state change | Toast; Status banner; Inline feedback | state.messageDuration |
| 161 | Disclosure Controls Expose Expanded State | Components: disclosure, overlays, and grouped interaction | Disclosure; Accordion; Details/summary; Filters panel | semantic.expanded |
| 162 | Disclosure Controls and Content Linked | Components: disclosure, overlays, and grouped interaction | Disclosure; Accordion; Filter panel | semantic.controls; semantic.labelledby |
| 163 | Collapsed Disclosure Content Removed Accessibly | Components: disclosure, overlays, and grouped interaction | Disclosure; Accordion; Filter panel | semantic.hidden; visibility.state |
| 164 | Revealed Content Follows Control Logically | Components: disclosure, overlays, and grouped interaction | Disclosure; Accordion; Filter panel | layout.order; semantic.order |
| 165 | Accordion Items Use Heading + Button Pattern | Components: disclosure, overlays, and grouped interaction | Accordion | semantic.heading; semantic.button; typography.heading.* |
| 166 | Single-Select Accordions Enforce One Open Item | Components: disclosure, overlays, and grouped interaction | Accordion | state.selectionMode; semantic.expanded |
| 167 | Tabs Use Correct Roles When Enhanced | Components: disclosure, overlays, and grouped interaction | Tabs | semantic.tablist; semantic.tab; semantic.tabpanel |
| 168 | Tabs Preserve Non-JavaScript Access | Components: disclosure, overlays, and grouped interaction | Tabs | routing.fragment; semantic.linkFallback |
| 169 | Only Active Tab Panel Exposed | Components: disclosure, overlays, and grouped interaction | Tabs | semantic.hidden; semantic.selected |
| 170 | Information Panels Open and Close Predictably | Components: disclosure, overlays, and grouped interaction | Info panel; Drawer; Popover | focus.programmatic; focus.returnTarget; state.open |
| 171 | Information Panels Not Used for Essential-Only Content | Components: disclosure, overlays, and grouped interaction | Info panel; Drawer; Popover | content.essentialFallback |
| 172 | Modal Dialog Announces Identity and Modality | Components: disclosure, overlays, and grouped interaction | Modal; Alert dialog | semantic.dialog; semantic.modal; content.dialogTitle |
| 173 | Modal Dialog Blocks Background Interaction | Components: disclosure, overlays, and grouped interaction | Modal; Alert dialog | focus.trap; state.inertBackground |
| 174 | Modal Dialog Has Accessible Close Method | Components: disclosure, overlays, and grouped interaction | Modal; Alert dialog | content.actionLabel; keyboard.binding |
| 175 | Modal Dialog Content Fits or Scrolls | Components: disclosure, overlays, and grouped interaction | Modal; Alert dialog | layout.dialogMaxHeight; layout.overflow |
| 176 | Action Dialog Uses Buttons vs Links Appropriately | Components: disclosure, overlays, and grouped interaction | Modal; Confirmation dialog | semantic.button; semantic.link |
| 177 | Mega Menu Trigger Uses Button Semantics | Components: disclosure, overlays, and grouped interaction | Mega menu | semantic.button; content.actionLabel |
| 178 | Mega Menu Closes on Escape, Blur, or Outside Click | Components: disclosure, overlays, and grouped interaction | Mega menu | keyboard.binding; state.dismissPolicy |
| 179 | Carousel Is Entirely User Driven | Components: disclosure, overlays, and grouped interaction | Carousel | motion.autoAdvance; controls.previousNext |
| 180 | Carousel Hidden or Faint Items Not Presented as Fully Available | Components: disclosure, overlays, and grouped interaction | Carousel | state.visibility; semantic.hidden |
| 181 | Native Media Controls or Accessible Equivalent Present | Media, promos, cards, comments, and rich content patterns | Audio player; Video player | media.controls; semantic.mediaControl |
| 182 | Media Does Not Autoplay Unexpectedly | Media, promos, cards, comments, and rich content patterns | Audio player; Video player; Promo media | media.autoplay |
| 183 | Captions Available for Spoken Video | Media, promos, cards, comments, and rich content patterns | Video player | media.caption; content.transcript |
| 184 | Audio Description or Equivalent for Essential Visual Information | Media, promos, cards, comments, and rich content patterns | Video player; Rich media | media.audioDescription; content.longDescription |
| 185 | Promo Has One Clear Primary Action | Media, promos, cards, comments, and rich content patterns | Promo; Hero; Teaser | content.actionLabel; layout.ctaPriority |
| 186 | Promo Headline Consistent With Destination | Media, promos, cards, comments, and rich content patterns | Promo; Hero; Teaser | content.heading; routing.destinationLabel |
| 187 | Promo Media Indicators Explained Non-Visually | Media, promos, cards, comments, and rich content patterns | Promo; Video teaser | content.mediaTypeLabel; content.durationText |
| 188 | Card Collections Use List Structure | Media, promos, cards, comments, and rich content patterns | Card collection; Search results; Promo grid | semantic.list; spacing.stack |
| 189 | Card Headline Comes First in Source Order | Media, promos, cards, comments, and rich content patterns | Card; Promo card; Article teaser | semantic.order; content.heading |
| 190 | Card Expandable Regions Follow Toggle State | Media, promos, cards, comments, and rich content patterns | Expandable card | semantic.expanded; semantic.controls |
| 191 | Comment Stream Uses Nested Structure for Replies | Media, promos, cards, comments, and rich content patterns | Comment stream; Forum thread | semantic.list; semantic.nesting |
| 192 | Comment Submission Feedback Accessible | Media, promos, cards, comments, and rich content patterns | Comment form; Thread composer | aria.live; content.statusText |
| 193 | Comment Controls Clearly Labelled | Media, promos, cards, comments, and rich content patterns | Comment actions; Reply; Vote; Share; Overflow | content.actionLabel; icon.semantic |
| 194 | Character Limits Communicated During Comment Entry | Media, promos, cards, comments, and rich content patterns | Comment input; Textarea | content.counterText; aria.live |
| 195 | Rating Displays Express Value in Text | Media, promos, cards, comments, and rich content patterns | Rating display; Review summary | content.valueText |
| 196 | Interactive Ratings Use Semantic Form Controls | Media, promos, cards, comments, and rich content patterns | Rating input | semantic.radio; semantic.range |
| 197 | Time Limits Can Be Extended, Disabled, or Adjusted | Time, persistence, and system behaviour | Session timeout; Quiz; Purchase flow; Verification flow | state.timeout; content.timeoutControl |
| 198 | Timeout Warning Issued Before Expiry | Time, persistence, and system behaviour | Session timeout; Purchase flow | state.timeout; content.timeoutWarning; aria.live |
| 199 | Timeout Consequences Communicated | Time, persistence, and system behaviour | Session timeout; Purchase flow; Draft editor | content.timeoutWarning; content.consequenceText |
| 200 | Unexpected Context Changes Prevented | Time, persistence, and system behaviour | Form; Navigation; Select; SPA route; Search filter | state.changePolicy; routing.routeName; semantic.submit |

## 2) Component -> required tests

| Component / pattern | Required tests |
|---|---|
| Accordion | 22. Motion Respects Reduced Motion Preference; 56. Heading Levels Follow Logical Hierarchy; 157. State Changes Reflected Programmatically; 161. Disclosure Controls Expose Expanded State; 162. Disclosure Controls and Content Linked; 163. Collapsed Disclosure Content Removed Accessibly; 164. Revealed Content Follows Control Logically; 165. Accordion Items Use Heading + Button Pattern; 166. Single-Select Accordions Enforce One Open Item |
| Address form | 118. Autocomplete Used for Personal Data Where Appropriate |
| Address group | 80. Group Labels for Related Controls; 119. Related Inputs Grouped Semantically |
| Alert | 1. Information Not Conveyed by Colour Alone; 2. Error States Not Conveyed by Colour Alone; 32. Notification Sound Supplemented by Another Modality; 102. Programmatic Focus Uses Appropriate Targets |
| Alert dialog | 172. Modal Dialog Announces Identity and Modality; 173. Modal Dialog Blocks Background Interaction; 174. Modal Dialog Has Accessible Close Method; 175. Modal Dialog Content Fits or Scrolls |
| Alert text | 8. Text Contrast Minimum |
| All components | 21. Content Usable Under Magnification |
| All interactive components | 5. Focus State Not Conveyed by Colour Alone; 10. Focus Indicator Contrast; 18. No Functional Loss on Resize; 61. Tab Order Aligns With Logical Structure; 91. All Interactive Elements Reachable by Keyboard; 92. All Interactive Elements Operable by Keyboard; 95. Focus Indicator Always Visible; 96. Focus Indicator Not Suppressed Without Equivalent; 104. Positive Tabindex Avoided; 107. Alternative Input Method Support |
| All text-bearing components | 14. Text Resizes to 200 Percent; 15. Text Resizes Beyond 200 Percent Where Supported |
| Ambient effects | 25. Decorative Animation Time-Limited |
| Animated banner | 24. Auto-Moving Content Can Be Stopped or Hidden |
| Animation | 26. Flashing Content Frequency Safety |
| Animation panel | 27. Flickering Content Warning and Alternative |
| Any form control | 77. Title Attribute Not Used as Primary Label |
| App shell | 20. Zoom Capability Preserved; 41. Primary Page Language Declared; 52. Skip Link or Equivalent Bypass Present; 154. Standard OS or Platform Notifications Used When Appropriate |
| App store link | 140. Download or Alternate Format Links Identified |
| Article | 16. Layout Reflows Without Horizontal Dependency; 19. Text Spacing Override Support; 42. Inline Language Changes Marked; 54. Heading Structure Present; 55. One Primary Heading Per Page Context; 56. Heading Levels Follow Logical Hierarchy |
| Article teaser | 189. Card Headline Comes First in Source Order |
| Aside | 49. Major Regions Use Appropriate Landmarks; 89. Breakout and Complementary Sections Uniquely Labelled |
| Asides | 50. Landmark Labels Distinguish Similar Regions |
| Audio player | 28. Autoplay Audio Control; 181. Native Media Controls or Accessible Equivalent Present; 182. Media Does Not Autoplay Unexpectedly |
| Autocomplete | 146. Search Suggestions Announced Accessibly |
| Autosave | 156. Focus Not Stolen by Non-Critical Updates |
| Avatar | 40. Supplementary Visual Cues Do Not Replace Meaningful Text |
| Background media | 33. Decorative Images Ignored by Assistive Technology |
| Badge | 17. No Text Clipping on Resize; 37. Images of Text Avoided |
| Banner | 38. Background Images with Meaning Have Equivalent Content |
| Body text | 8. Text Contrast Minimum; 13. Legibility Under Blur or Reduced Clarity |
| Breadcrumb | 86. Breadcrumb Current Item Labelled Correctly; 87. Current Navigation Item Exposed; 98. Focus Order Logical Through Navigation; 136. Link Purpose Understandable in Isolation; 141. Breadcrumbs Structured as Navigation List; 142. Breadcrumb Current Page Is Not an Active Link; 144. Current Navigation State Programmatically Exposed |
| Button | 11. Control Boundary Contrast; 17. No Text Clipping on Resize; 71. Interactive Elements Have Accessible Names; 73. Accessible Name Matches Visible Label; 81. Control Text Describes Purpose; 93. Standard Keyboard Activation Preserved; 110. Target Size Meets Minimum Usability Threshold |
| Button text | 8. Text Contrast Minimum |
| CTA | 81. Control Text Describes Purpose; 84. External Navigation Warns of Context Change; 85. New Window or New Tab Behaviour Disclosed; 139. External Link Warning Included |
| Card | 17. No Text Clipping on Resize; 37. Images of Text Avoided; 38. Background Images with Meaning Have Equivalent Content; 60. Source Order Matches Intended Reading Order; 138. Adjacent Duplicate Links Consolidated; 189. Card Headline Comes First in Source Order |
| Card action | 11. Control Boundary Contrast |
| Card collection | 63. Related Thematic Items Use List Semantics; 188. Card Collections Use List Structure |
| Card headline | 57. Heading Text Is Descriptive |
| Card link | 6. Link Identification Not Conveyed by Colour Alone; 136. Link Purpose Understandable in Isolation |
| Card list | 62. CSS Reordering Does Not Break Meaning |
| Card media | 34. Informative Images Have Equivalent Text |
| Card selector | 4. Selection State Not Conveyed by Colour Alone |
| Cards | 137. Repeated Link Text Distinguishable Where Destinations Differ |
| Carousel | 22. Motion Respects Reduced Motion Preference; 23. Auto-Moving Content Can Be Paused; 24. Auto-Moving Content Can Be Stopped or Hidden; 94. No Keyboard Trap; 108. Gesture Functions Have Non-Gesture Alternatives; 179. Carousel Is Entirely User Driven; 180. Carousel Hidden or Faint Items Not Presented as Fully Available |
| Carousel video | 29. Autoplay Video Control |
| Chart | 1. Information Not Conveyed by Colour Alone; 7. Data Series Not Differentiated Only by Colour; 36. Complex Visuals Have Summary |
| Checkbox | 3. Required States Not Conveyed by Colour Alone; 11. Control Boundary Contrast; 71. Interactive Elements Have Accessible Names; 74. Label Is Near the Control It Describes; 93. Standard Keyboard Activation Preserved; 157. State Changes Reflected Programmatically |
| Checkbox group | 80. Group Labels for Related Controls; 113. Required Fields Indicated Programmatically; 114. Required Fields Indicated Visually; 121. Checkbox Sets Grouped Where They Share a Question |
| Checkout | 97. Focus Order Logical Through Forms; 122. Error Messages Shown When Submission Fails; 127. Error Summary Provided for Multiple Errors; 129. User Input Preserved After Validation Failure |
| Chip | 110. Target Size Meets Minimum Usability Threshold |
| Columns | 64. Arbitrary Layout Containers Avoid False Semantics |
| Combobox | 99. Focus Does Not Move Unexpectedly During Input |
| Comment | 42. Inline Language Changes Marked |
| Comment actions | 193. Comment Controls Clearly Labelled |
| Comment form | 111. Explicit Submit Control Present; 122. Error Messages Shown When Submission Fails; 129. User Input Preserved After Validation Failure; 192. Comment Submission Feedback Accessible |
| Comment input | 194. Character Limits Communicated During Comment Entry |
| Comment stream | 191. Comment Stream Uses Nested Structure for Replies |
| Comment thread | 43. Language Direction Specified When Needed |
| Comments | 63. Related Thematic Items Use List Semantics; 155. Dynamic Content Discoverable After Update |
| Comments region | 90. Comments, Panels, and Supplemental Regions Clearly Named |
| Comparison table | 65. Tables Used Only for Tabular Data; 69. Table Remains Structurally Intact on Small Screens |
| Confirmation dialog | 176. Action Dialog Uses Buttons vs Links Appropriately |
| Confirmation failure | 152. Critical Alerts Perceivable in Multiple Modalities |
| Critical alert | 152. Critical Alerts Perceivable in Multiple Modalities |
| Custom controls | 105. Tabindex Zero Used Only on Intended Interactive Targets |
| Data display | 16. Layout Reflows Without Horizontal Dependency |
| Data table | 13. Legibility Under Blur or Reduced Clarity; 65. Tables Used Only for Tabular Data; 66. Data Tables Include Header Cells; 67. Data Table Header Scope Defined; 68. Data Tables Include Caption |
| Date chip | 88. Metadata Values Clarified Non-Visually |
| Date input | 78. Instructions Associated With Relevant Field; 116. Input Format Expectations Communicated; 117. Appropriate Input Type Used |
| Decorative animation | 25. Decorative Animation Time-Limited |
| Dense menus | 109. Pointer Precision Not Required for Basic Tasks |
| Details/summary | 161. Disclosure Controls Expose Expanded State |
| Diagram | 36. Complex Visuals Have Summary |
| Dialog | 54. Heading Structure Present; 56. Heading Levels Follow Logical Hierarchy; 100. Focus Moves to New Context on Open; 101. Focus Returns on Close |
| Dialog heading | 106. Tabindex Minus One Used for Programmatic Focus Only |
| Disclosure | 157. State Changes Reflected Programmatically; 161. Disclosure Controls Expose Expanded State; 162. Disclosure Controls and Content Linked; 163. Collapsed Disclosure Content Removed Accessibly; 164. Revealed Content Follows Control Logically |
| Divider illustration | 33. Decorative Images Ignored by Assistive Technology |
| Document root | 41. Primary Page Language Declared |
| Download link | 85. New Window or New Tab Behaviour Disclosed; 140. Download or Alternate Format Links Identified |
| Draft editor | 199. Timeout Consequences Communicated |
| Drag/drop | 108. Gesture Functions Have Non-Gesture Alternatives |
| Drawer | 90. Comments, Panels, and Supplemental Regions Clearly Named; 100. Focus Moves to New Context on Open; 101. Focus Returns on Close; 170. Information Panels Open and Close Predictably; 171. Information Panels Not Used for Essential-Only Content |
| Duration | 88. Metadata Values Clarified Non-Visually |
| Editor | 94. No Keyboard Trap |
| Email input | 117. Appropriate Input Type Used |
| Entire form journey | 133. Form Completion Possible by Keyboard Only |
| Error summary | 2. Error States Not Conveyed by Colour Alone; 79. Error Messages Associated With Relevant Field; 102. Programmatic Focus Uses Appropriate Targets; 106. Tabindex Minus One Used for Programmatic Focus Only; 123. Error Messages Are Announced to Assistive Technology; 124. Error Message Identifies the Relevant Field; 125. Error Message Explains the Problem; 126. Error Message Tells User How to Fix It; 128. Error Summary Supports Navigation to Fields; 131. Error Cues Persist Long Enough to Be Used |
| Error text | 19. Text Spacing Override Support |
| Expand-on-load section | 155. Dynamic Content Discoverable After Update |
| Expandable card | 190. Card Expandable Regions Follow Toggle State |
| External link | 84. External Navigation Warns of Context Change; 139. External Link Warning Included |
| Fieldset | 80. Group Labels for Related Controls; 119. Related Inputs Grouped Semantically |
| Figure | 34. Informative Images Have Equivalent Text |
| Filter | 144. Current Navigation State Programmatically Exposed |
| Filter bar | 112. Submission Occurs Only on Explicit Action |
| Filter chip | 1. Information Not Conveyed by Colour Alone |
| Filter chips | 87. Current Navigation Item Exposed |
| Filter panel | 162. Disclosure Controls and Content Linked; 163. Collapsed Disclosure Content Removed Accessibly; 164. Revealed Content Follows Control Logically |
| Filters panel | 161. Disclosure Controls Expose Expanded State |
| Floating label field | 75. Label Remains Available During Input |
| Footer | 49. Major Regions Use Appropriate Landmarks |
| Footer link | 136. Link Purpose Understandable in Isolation; 139. External Link Warning Included |
| Footer nav | 143. Navigation Menus Use Correct Structural Semantics |
| Form | 16. Layout Reflows Without Horizontal Dependency; 54. Heading Structure Present; 60. Source Order Matches Intended Reading Order; 61. Tab Order Aligns With Logical Structure; 62. CSS Reordering Does Not Break Meaning; 97. Focus Order Logical Through Forms; 99. Focus Does Not Move Unexpectedly During Input; 111. Explicit Submit Control Present; 112. Submission Occurs Only on Explicit Action; 122. Error Messages Shown When Submission Fails; 123. Error Messages Are Announced to Assistive Technology; 129. User Input Preserved After Validation Failure; 132. Reset Buttons Avoided or Safe; 200. Unexpected Context Changes Prevented |
| Form field | 2. Error States Not Conveyed by Colour Alone; 74. Label Is Near the Control It Describes; 78. Instructions Associated With Relevant Field; 79. Error Messages Associated With Relevant Field; 115. Optional Fields Marked Where Pattern Requires; 124. Error Message Identifies the Relevant Field; 125. Error Message Explains the Problem; 126. Error Message Tells User How to Fix It; 130. Validation Does Not Interrupt Every Keystroke Inappropriately |
| Form help | 19. Text Spacing Override Support |
| Form labels | 13. Legibility Under Blur or Reduced Clarity |
| Form submit | 158. State Change Announced When It Matters |
| Forum thread | 191. Comment Stream Uses Nested Structure for Replies |
| Global nav | 52. Skip Link or Equivalent Bypass Present; 143. Navigation Menus Use Correct Structural Semantics |
| Graph | 7. Data Series Not Differentiated Only by Colour |
| Grid | 62. CSS Reordering Does Not Break Meaning; 64. Arbitrary Layout Containers Avoid False Semantics |
| Group label | 3. Required States Not Conveyed by Colour Alone |
| Header | 49. Major Regions Use Appropriate Landmarks |
| Header nav | 98. Focus Order Logical Through Navigation |
| Heading | 9. Large Text Contrast Minimum; 13. Legibility Under Blur or Reduced Clarity; 57. Heading Text Is Descriptive; 59. Headings Are Visually Distinguishable |
| Heading component | 58. Visual Headings Match Semantic Headings |
| Help panel | 83. Supplementary Help Does Not Duplicate Primary Name |
| Hero | 38. Background Images with Meaning Have Equivalent Content; 185. Promo Has One Clear Primary Action; 186. Promo Headline Consistent With Destination |
| Hero banner | 37. Images of Text Avoided |
| Hero media | 29. Autoplay Video Control |
| Hero motion | 25. Decorative Animation Time-Limited |
| Hero text | 9. Large Text Contrast Minimum |
| Hidden utility link | 103. Hidden Focusable Elements Revealed on Focus |
| Hint text | 83. Supplementary Help Does Not Duplicate Primary Name |
| Icon | 33. Decorative Images Ignored by Assistive Technology |
| Icon button | 82. Icon-Only Controls Have Equivalent Text |
| Icon label | 40. Supplementary Visual Cues Do Not Replace Meaningful Text |
| Icon-only control | 77. Title Attribute Not Used as Primary Label |
| Iconic control | 35. Functional Images Describe Action |
| Image | 33. Decorative Images Ignored by Assistive Technology; 34. Informative Images Have Equivalent Text |
| Image button | 35. Functional Images Describe Action |
| Infinite list | 155. Dynamic Content Discoverable After Update |
| Info panel | 101. Focus Returns on Close; 170. Information Panels Open and Close Predictably; 171. Information Panels Not Used for Essential-Only Content |
| Infographic | 36. Complex Visuals Have Summary |
| Inline feedback | 160. Update Timing Allows Perception |
| Inline link | 6. Link Identification Not Conveyed by Colour Alone; 136. Link Purpose Understandable in Isolation |
| Inline quote | 42. Inline Language Changes Marked |
| Inline success | 151. Status Messages Announced Without Forced Focus Change |
| Inline validation | 2. Error States Not Conveyed by Colour Alone; 79. Error Messages Associated With Relevant Field; 123. Error Messages Are Announced to Assistive Technology; 131. Error Cues Persist Long Enough to Be Used |
| Input | 3. Required States Not Conveyed by Colour Alone; 11. Control Boundary Contrast; 12. Placeholder Contrast Adequacy; 17. No Text Clipping on Resize; 43. Language Direction Specified When Needed; 71. Interactive Elements Have Accessible Names; 72. Visible Labels Exist for Form Inputs; 73. Accessible Name Matches Visible Label; 75. Label Remains Available During Input; 76. Placeholder Does Not Replace Label; 113. Required Fields Indicated Programmatically; 114. Required Fields Indicated Visually |
| Label | 8. Text Contrast Minimum |
| Large button label | 9. Large Text Contrast Minimum |
| Layout | 14. Text Resizes to 200 Percent; 15. Text Resizes Beyond 200 Percent Where Supported; 16. Layout Reflows Without Horizontal Dependency; 18. No Functional Loss on Resize; 20. Zoom Capability Preserved; 21. Content Usable Under Magnification; 60. Source Order Matches Intended Reading Order |
| Layout shell | 48. One Main Landmark Per Page; 51. Content Belongs to Defined Regions |
| Layout wrapper | 64. Arbitrary Layout Containers Avoid False Semantics |
| Legend | 7. Data Series Not Differentiated Only by Colour |
| Link | 71. Interactive Elements Have Accessible Names; 73. Accessible Name Matches Visible Label; 81. Control Text Describes Purpose; 85. New Window or New Tab Behaviour Disclosed; 93. Standard Keyboard Activation Preserved; 110. Target Size Meets Minimum Usability Threshold |
| Link text | 8. Text Contrast Minimum |
| Listbox | 4. Selection State Not Conveyed by Colour Alone |
| Lists of links | 137. Repeated Link Text Distinguishable Where Destinations Differ |
| Long form | 127. Error Summary Provided for Multiple Errors |
| Long-form text | 19. Text Spacing Override Support |
| Main | 49. Major Regions Use Appropriate Landmarks |
| Main content container | 53. Skip Link Focuses Main Content Reliably |
| Main target | 106. Tabindex Minus One Used for Programmatic Focus Only |
| Map | 36. Complex Visuals Have Summary; 108. Gesture Functions Have Non-Gesture Alternatives |
| Map controls | 109. Pointer Precision Not Required for Basic Tasks |
| Marquee | 23. Auto-Moving Content Can Be Paused |
| Media player | 27. Flickering Content Warning and Alternative; 30. Media Does Not Mask Assistive Technology Audio; 31. Separate Audio Streams Adjustable; 94. No Keyboard Trap |
| Media promo | 138. Adjacent Duplicate Links Consolidated |
| Mega menu | 143. Navigation Menus Use Correct Structural Semantics; 177. Mega Menu Trigger Uses Button Semantics; 178. Mega Menu Closes on Escape, Blur, or Outside Click |
| Menu | 4. Selection State Not Conveyed by Colour Alone; 87. Current Navigation Item Exposed; 94. No Keyboard Trap; 144. Current Navigation State Programmatically Exposed |
| Menu item | 71. Interactive Elements Have Accessible Names; 73. Accessible Name Matches Visible Label; 81. Control Text Describes Purpose; 93. Standard Keyboard Activation Preserved |
| Messaging UI | 43. Language Direction Specified When Needed |
| Metadata chip | 40. Supplementary Visual Cues Do Not Replace Meaningful Text |
| Modal | 22. Motion Respects Reduced Motion Preference; 60. Source Order Matches Intended Reading Order; 61. Tab Order Aligns With Logical Structure; 94. No Keyboard Trap; 100. Focus Moves to New Context on Open; 101. Focus Returns on Close; 102. Programmatic Focus Uses Appropriate Targets; 172. Modal Dialog Announces Identity and Modality; 173. Modal Dialog Blocks Background Interaction; 174. Modal Dialog Has Accessible Close Method; 175. Modal Dialog Content Fits or Scrolls; 176. Action Dialog Uses Buttons vs Links Appropriately |
| Multiple navs | 50. Landmark Labels Distinguish Similar Regions |
| Multitrack player | 31. Separate Audio Streams Adjustable |
| Native notification bridge | 154. Standard OS or Platform Notifications Used When Appropriate |
| Nav | 49. Major Regions Use Appropriate Landmarks; 61. Tab Order Aligns With Logical Structure |
| Nav item | 84. External Navigation Warns of Context Change |
| Nav list | 63. Related Thematic Items Use List Semantics |
| Navigation | 16. Layout Reflows Without Horizontal Dependency; 21. Content Usable Under Magnification; 200. Unexpected Context Changes Prevented |
| Navigation item | 1. Information Not Conveyed by Colour Alone; 17. No Text Clipping on Resize |
| Navigation link | 6. Link Identification Not Conveyed by Colour Alone |
| Navigation logo | 37. Images of Text Avoided |
| Navigation state | 46. Page Title Is Unique Within Context |
| Notification center | 153. Notifications Not Overbearing |
| Number input | 117. Appropriate Input Type Used |
| OTP | 116. Input Format Expectations Communicated; 134. Password and Complex Input Assistance Available |
| OTP input | 99. Focus Does Not Move Unexpectedly During Input |
| Off-canvas control | 103. Hidden Focusable Elements Revealed on Focus |
| Optional metadata | 115. Optional Fields Marked Where Pattern Requires |
| Overflow | 193. Comment Controls Clearly Labelled |
| Overflow menu | 147. Share and Auxiliary Tool Clarity |
| Overflow menu trigger | 82. Icon-Only Controls Have Equivalent Text |
| PDF link | 140. Download or Alternate Format Links Identified |
| Page header | 55. One Primary Heading Per Page Context |
| Page template | 41. Primary Page Language Declared; 44. Page Title Present; 45. Page Title Describes Primary Content; 46. Page Title Is Unique Within Context; 48. One Main Landmark Per Page; 51. Content Belongs to Defined Regions; 52. Skip Link or Equivalent Bypass Present |
| Pagination | 4. Selection State Not Conveyed by Colour Alone; 87. Current Navigation Item Exposed; 98. Focus Order Logical Through Navigation; 110. Target Size Meets Minimum Usability Threshold; 144. Current Navigation State Programmatically Exposed |
| Panels | 105. Tabindex Zero Used Only on Intended Interactive Targets |
| Password field | 78. Instructions Associated With Relevant Field; 116. Input Format Expectations Communicated; 126. Error Message Tells User How to Fix It; 130. Validation Does Not Interrupt Every Keystroke Inappropriately; 134. Password and Complex Input Assistance Available |
| Payment form | 118. Autocomplete Used for Personal Data Where Appropriate |
| Payment group | 119. Related Inputs Grouped Semantically |
| Phone input | 116. Input Format Expectations Communicated |
| Podcast player | 31. Separate Audio Streams Adjustable |
| Popover | 100. Focus Moves to New Context on Open; 101. Focus Returns on Close; 170. Information Panels Open and Close Predictably; 171. Information Panels Not Used for Essential-Only Content |
| Print | 147. Share and Auxiliary Tool Clarity |
| Profile form | 118. Autocomplete Used for Personal Data Where Appropriate |
| Progress indicator | 39. Visible Rating or Graphic Indicators Have Text Equivalent |
| Promo | 27. Flickering Content Warning and Alternative; 37. Images of Text Avoided; 38. Background Images with Meaning Have Equivalent Content; 60. Source Order Matches Intended Reading Order; 185. Promo Has One Clear Primary Action; 186. Promo Headline Consistent With Destination; 187. Promo Media Indicators Explained Non-Visually |
| Promo card | 189. Card Headline Comes First in Source Order |
| Promo grid | 188. Card Collections Use List Structure |
| Promo media | 28. Autoplay Audio Control; 182. Media Does Not Autoplay Unexpectedly |
| Promo media CTA | 35. Functional Images Describe Action |
| Promotional banner | 26. Flashing Content Frequency Safety |
| Purchase flow | 197. Time Limits Can Be Extended, Disabled, or Adjusted; 198. Timeout Warning Issued Before Expiry; 199. Timeout Consequences Communicated |
| Quiz | 197. Time Limits Can Be Extended, Disabled, or Adjusted |
| Radio | 3. Required States Not Conveyed by Colour Alone; 11. Control Boundary Contrast; 71. Interactive Elements Have Accessible Names; 93. Standard Keyboard Activation Preserved |
| Radio group | 74. Label Is Near the Control It Describes; 80. Group Labels for Related Controls; 120. Radio Groups Operate as One Logical Question |
| Rating display | 39. Visible Rating or Graphic Indicators Have Text Equivalent; 195. Rating Displays Express Value in Text |
| Rating input | 196. Interactive Ratings Use Semantic Form Controls |
| Registration | 127. Error Summary Provided for Multiple Errors |
| Related links | 89. Breakout and Complementary Sections Uniquely Labelled; 137. Repeated Link Text Distinguishable Where Destinations Differ |
| Reorder list | 108. Gesture Functions Have Non-Gesture Alternatives |
| Reply | 193. Comment Controls Clearly Labelled |
| Responsive table | 69. Table Remains Structurally Intact on Small Screens |
| Review summary | 39. Visible Rating or Graphic Indicators Have Text Equivalent; 195. Rating Displays Express Value in Text |
| Rich media | 184. Audio Description or Equivalent for Essential Visual Information |
| Rich text | 42. Inline Language Changes Marked; 43. Language Direction Specified When Needed; 58. Visual Headings Match Semantic Headings |
| Rotator | 23. Auto-Moving Content Can Be Paused |
| Route container | 44. Page Title Present; 45. Page Title Describes Primary Content; 46. Page Title Is Unique Within Context; 148. SPA Route Changes Update Focus Position |
| Route loader | 150. Route Change Loading State Communicated |
| Router | 47. SPA Title Updates on Route Change; 149. SPA Route Changes Update History |
| SPA route | 102. Programmatic Focus Uses Appropriate Targets; 200. Unexpected Context Changes Prevented |
| SPA shell | 44. Page Title Present; 47. SPA Title Updates on Route Change; 148. SPA Route Changes Update Focus Position; 149. SPA Route Changes Update History; 150. Route Change Loading State Communicated |
| Save | 147. Share and Auxiliary Tool Clarity |
| Save button | 135. Submit Controls Not Inaccessibly Disabled |
| Save state | 158. State Change Announced When It Matters |
| Scroll regions | 105. Tabindex Zero Used Only on Intended Interactive Targets |
| Scrollable table wrapper | 70. Scrollable Table Container Is Accessible |
| Search | 49. Major Regions Use Appropriate Landmarks |
| Search field | 12. Placeholder Contrast Adequacy; 72. Visible Labels Exist for Form Inputs; 76. Placeholder Does Not Replace Label; 130. Validation Does Not Interrupt Every Keystroke Inappropriately |
| Search filter | 200. Unexpected Context Changes Prevented |
| Search form | 111. Explicit Submit Control Present; 145. Search Region Identifiable |
| Search results | 63. Related Thematic Items Use List Semantics; 188. Card Collections Use List Structure |
| Search results header | 145. Search Region Identifiable |
| Search suggest | 146. Search Suggestions Announced Accessibly; 159. Live Regions Used Appropriately |
| Section | 56. Heading Levels Follow Logical Hierarchy |
| Section header | 57. Heading Text Is Descriptive; 58. Visual Headings Match Semantic Headings; 59. Headings Are Visually Distinguishable |
| Section wrapper | 51. Content Belongs to Defined Regions |
| Security question | 134. Password and Complex Input Assistance Available |
| Segmented control | 4. Selection State Not Conveyed by Colour Alone |
| Select | 3. Required States Not Conveyed by Colour Alone; 11. Control Boundary Contrast; 71. Interactive Elements Have Accessible Names; 72. Visible Labels Exist for Form Inputs; 112. Submission Occurs Only on Explicit Action; 113. Required Fields Indicated Programmatically; 114. Required Fields Indicated Visually; 200. Unexpected Context Changes Prevented |
| Selection | 158. State Change Announced When It Matters |
| Session timeout | 197. Time Limits Can Be Extended, Disabled, or Adjusted; 198. Timeout Warning Issued Before Expiry; 199. Timeout Consequences Communicated |
| Settings form | 132. Reset Buttons Avoided or Safe |
| Settings page | 54. Heading Structure Present |
| Share | 193. Comment Controls Clearly Labelled |
| Share tools | 90. Comments, Panels, and Supplemental Regions Clearly Named; 147. Share and Auxiliary Tool Clarity |
| Sidebar layout | 62. CSS Reordering Does Not Break Meaning |
| Sidebar nav | 98. Focus Order Logical Through Navigation; 143. Navigation Menus Use Correct Structural Semantics |
| Skeleton | 150. Route Change Loading State Communicated |
| Skip link | 53. Skip Link Focuses Main Content Reliably; 103. Hidden Focusable Elements Revealed on Focus |
| Slider | 108. Gesture Functions Have Non-Gesture Alternatives |
| Small icon buttons | 109. Pointer Precision Not Required for Basic Tasks |
| Source metadata | 88. Metadata Values Clarified Non-Visually |
| Stats | 88. Metadata Values Clarified Non-Visually |
| Status area | 159. Live Regions Used Appropriately |
| Status badge | 1. Information Not Conveyed by Colour Alone; 40. Supplementary Visual Cues Do Not Replace Meaningful Text |
| Status banner | 151. Status Messages Announced Without Forced Focus Change; 160. Update Timing Allows Perception |
| Submit button | 135. Submit Controls Not Inaccessibly Disabled |
| Suggestion update | 156. Focus Not Stolen by Non-Critical Updates |
| Supplemental panel | 89. Breakout and Complementary Sections Uniquely Labelled; 90. Comments, Panels, and Supplemental Regions Clearly Named |
| System alert | 152. Critical Alerts Perceivable in Multiple Modalities |
| System audio UI | 30. Media Does Not Mask Assistive Technology Audio |
| System notification | 32. Notification Sound Supplemented by Another Modality |
| Tabs | 1. Information Not Conveyed by Colour Alone; 4. Selection State Not Conveyed by Colour Alone; 87. Current Navigation Item Exposed; 144. Current Navigation State Programmatically Exposed; 157. State Changes Reflected Programmatically; 167. Tabs Use Correct Roles When Enhanced; 168. Tabs Preserve Non-JavaScript Access; 169. Only Active Tab Panel Exposed |
| Tag | 17. No Text Clipping on Resize |
| Teaser | 138. Adjacent Duplicate Links Consolidated; 185. Promo Has One Clear Primary Action; 186. Promo Headline Consistent With Destination |
| Tel input | 117. Appropriate Input Type Used |
| Textarea | 12. Placeholder Contrast Adequacy; 72. Visible Labels Exist for Form Inputs; 75. Label Remains Available During Input; 76. Placeholder Does Not Replace Label; 113. Required Fields Indicated Programmatically; 114. Required Fields Indicated Visually; 194. Character Limits Communicated During Comment Entry |
| Thread composer | 192. Comment Submission Feedback Accessible |
| Ticker | 23. Auto-Moving Content Can Be Paused; 24. Auto-Moving Content Can Be Stopped or Hidden |
| Toast | 22. Motion Respects Reduced Motion Preference; 32. Notification Sound Supplemented by Another Modality; 131. Error Cues Persist Long Enough to Be Used; 151. Status Messages Announced Without Forced Focus Change; 156. Focus Not Stolen by Non-Critical Updates; 159. Live Regions Used Appropriately; 160. Update Timing Allows Perception |
| Toast system | 153. Notifications Not Overbearing |
| Toggle | 71. Interactive Elements Have Accessible Names; 73. Accessible Name Matches Visible Label; 110. Target Size Meets Minimum Usability Threshold; 157. State Changes Reflected Programmatically; 158. State Change Announced When It Matters |
| Toolbar action | 82. Icon-Only Controls Have Equivalent Text |
| Tooltip | 22. Motion Respects Reduced Motion Preference; 83. Supplementary Help Does Not Duplicate Primary Name |
| Transitions | 22. Motion Respects Reduced Motion Preference |
| Tree | 157. State Changes Reflected Programmatically |
| Typeahead | 146. Search Suggestions Announced Accessibly |
| Validation state | 1. Information Not Conveyed by Colour Alone |
| Verification flow | 197. Time Limits Can Be Extended, Disabled, or Adjusted |
| Video | 26. Flashing Content Frequency Safety |
| Video player | 28. Autoplay Audio Control; 29. Autoplay Video Control; 181. Native Media Controls or Accessible Equivalent Present; 182. Media Does Not Autoplay Unexpectedly; 183. Captions Available for Spoken Video; 184. Audio Description or Equivalent for Essential Visual Information |
| Video teaser | 187. Promo Media Indicators Explained Non-Visually |
| View container | 47. SPA Title Updates on Route Change; 55. One Primary Heading Per Page Context |
| Viewport | 20. Zoom Capability Preserved |
| Vote | 193. Comment Controls Clearly Labelled |
| Wizard | 97. Focus Order Logical Through Forms |
| complementary regions | 50. Landmark Labels Distinguish Similar Regions |

## 3) Test -> impacted components

| ID | Canonical test | Impacted components / patterns |
|---:|---|---|
| 1 | Information Not Conveyed by Colour Alone | Status badge; Alert; Validation state; Chart; Filter chip; Tabs; Navigation item |
| 2 | Error States Not Conveyed by Colour Alone | Form field; Error summary; Inline validation; Alert |
| 3 | Required States Not Conveyed by Colour Alone | Input; Select; Checkbox; Radio; Group label |
| 4 | Selection State Not Conveyed by Colour Alone | Tabs; Segmented control; Listbox; Menu; Card selector; Pagination |
| 5 | Focus State Not Conveyed by Colour Alone | All interactive components |
| 6 | Link Identification Not Conveyed by Colour Alone | Inline link; Navigation link; Card link |
| 7 | Data Series Not Differentiated Only by Colour | Chart; Graph; Legend |
| 8 | Text Contrast Minimum | Body text; Label; Button text; Link text; Alert text |
| 9 | Large Text Contrast Minimum | Heading; Hero text; Large button label |
| 10 | Focus Indicator Contrast | All interactive components |
| 11 | Control Boundary Contrast | Button; Input; Select; Checkbox; Radio; Card action |
| 12 | Placeholder Contrast Adequacy | Input; Textarea; Search field |
| 13 | Legibility Under Blur or Reduced Clarity | Body text; Heading; Data table; Form labels |
| 14 | Text Resizes to 200 Percent | All text-bearing components; Layout |
| 15 | Text Resizes Beyond 200 Percent Where Supported | All text-bearing components; Layout |
| 16 | Layout Reflows Without Horizontal Dependency | Layout; Article; Form; Navigation; Data display |
| 17 | No Text Clipping on Resize | Button; Input; Tag; Badge; Navigation item; Card |
| 18 | No Functional Loss on Resize | All interactive components; Layout |
| 19 | Text Spacing Override Support | Article; Long-form text; Form help; Error text |
| 20 | Zoom Capability Preserved | App shell; Viewport; Layout |
| 21 | Content Usable Under Magnification | All components; Layout; Navigation |
| 22 | Motion Respects Reduced Motion Preference | Carousel; Modal; Toast; Accordion; Tooltip; Transitions |
| 23 | Auto-Moving Content Can Be Paused | Carousel; Marquee; Ticker; Rotator |
| 24 | Auto-Moving Content Can Be Stopped or Hidden | Carousel; Ticker; Animated banner |
| 25 | Decorative Animation Time-Limited | Decorative animation; Hero motion; Ambient effects |
| 26 | Flashing Content Frequency Safety | Animation; Video; Promotional banner |
| 27 | Flickering Content Warning and Alternative | Media player; Promo; Animation panel |
| 28 | Autoplay Audio Control | Audio player; Video player; Promo media |
| 29 | Autoplay Video Control | Video player; Carousel video; Hero media |
| 30 | Media Does Not Mask Assistive Technology Audio | Media player; System audio UI |
| 31 | Separate Audio Streams Adjustable | Media player; Podcast player; Multitrack player |
| 32 | Notification Sound Supplemented by Another Modality | Toast; Alert; System notification |
| 33 | Decorative Images Ignored by Assistive Technology | Image; Icon; Divider illustration; Background media |
| 34 | Informative Images Have Equivalent Text | Image; Figure; Card media |
| 35 | Functional Images Describe Action | Image button; Promo media CTA; Iconic control |
| 36 | Complex Visuals Have Summary | Chart; Diagram; Infographic; Map |
| 37 | Images of Text Avoided | Hero banner; Promo; Card; Badge; Navigation logo |
| 38 | Background Images with Meaning Have Equivalent Content | Hero; Promo; Banner; Card |
| 39 | Visible Rating or Graphic Indicators Have Text Equivalent | Rating display; Review summary; Progress indicator |
| 40 | Supplementary Visual Cues Do Not Replace Meaningful Text | Status badge; Avatar; Icon label; Metadata chip |
| 41 | Primary Page Language Declared | App shell; Page template; Document root |
| 42 | Inline Language Changes Marked | Rich text; Article; Comment; Inline quote |
| 43 | Language Direction Specified When Needed | Rich text; Input; Comment thread; Messaging UI |
| 44 | Page Title Present | Page template; Route container; SPA shell |
| 45 | Page Title Describes Primary Content | Page template; Route container |
| 46 | Page Title Is Unique Within Context | Page template; Route container; Navigation state |
| 47 | SPA Title Updates on Route Change | SPA shell; Router; View container |
| 48 | One Main Landmark Per Page | Page template; Layout shell |
| 49 | Major Regions Use Appropriate Landmarks | Header; Nav; Main; Footer; Aside; Search |
| 50 | Landmark Labels Distinguish Similar Regions | Multiple navs; Asides; complementary regions |
| 51 | Content Belongs to Defined Regions | Page template; Layout shell; Section wrapper |
| 52 | Skip Link or Equivalent Bypass Present | Page template; Global nav; App shell |
| 53 | Skip Link Focuses Main Content Reliably | Skip link; Main content container |
| 54 | Heading Structure Present | Article; Form; Settings page; Dialog |
| 55 | One Primary Heading Per Page Context | Page header; Article; View container |
| 56 | Heading Levels Follow Logical Hierarchy | Section; Accordion; Dialog; Article |
| 57 | Heading Text Is Descriptive | Heading; Section header; Card headline |
| 58 | Visual Headings Match Semantic Headings | Heading component; Rich text; Section header |
| 59 | Headings Are Visually Distinguishable | Heading; Section header |
| 60 | Source Order Matches Intended Reading Order | Card; Promo; Layout; Modal; Form |
| 61 | Tab Order Aligns With Logical Structure | All interactive components; Form; Nav; Modal |
| 62 | CSS Reordering Does Not Break Meaning | Grid; Card list; Sidebar layout; Form |
| 63 | Related Thematic Items Use List Semantics | Card collection; Nav list; Comments; Search results |
| 64 | Arbitrary Layout Containers Avoid False Semantics | Grid; Columns; Layout wrapper |
| 65 | Tables Used Only for Tabular Data | Data table; Comparison table |
| 66 | Data Tables Include Header Cells | Data table |
| 67 | Data Table Header Scope Defined | Data table |
| 68 | Data Tables Include Caption | Data table |
| 69 | Table Remains Structurally Intact on Small Screens | Responsive table; Comparison table |
| 70 | Scrollable Table Container Is Accessible | Scrollable table wrapper |
| 71 | Interactive Elements Have Accessible Names | Button; Link; Input; Select; Checkbox; Radio; Toggle; Menu item |
| 72 | Visible Labels Exist for Form Inputs | Input; Select; Textarea; Search field |
| 73 | Accessible Name Matches Visible Label | Input; Button; Link; Toggle; Menu item |
| 74 | Label Is Near the Control It Describes | Form field; Checkbox; Radio group |
| 75 | Label Remains Available During Input | Floating label field; Input; Textarea |
| 76 | Placeholder Does Not Replace Label | Input; Search field; Textarea |
| 77 | Title Attribute Not Used as Primary Label | Any form control; Icon-only control |
| 78 | Instructions Associated With Relevant Field | Form field; Password field; Date input |
| 79 | Error Messages Associated With Relevant Field | Form field; Error summary; Inline validation |
| 80 | Group Labels for Related Controls | Fieldset; Radio group; Checkbox group; Address group |
| 81 | Control Text Describes Purpose | Button; Link; Menu item; CTA |
| 82 | Icon-Only Controls Have Equivalent Text | Icon button; Toolbar action; Overflow menu trigger |
| 83 | Supplementary Help Does Not Duplicate Primary Name | Tooltip; Hint text; Help panel |
| 84 | External Navigation Warns of Context Change | External link; Nav item; CTA |
| 85 | New Window or New Tab Behaviour Disclosed | Link; CTA; Download link |
| 86 | Breadcrumb Current Item Labelled Correctly | Breadcrumb |
| 87 | Current Navigation Item Exposed | Tabs; Menu; Breadcrumb; Filter chips; Pagination |
| 88 | Metadata Values Clarified Non-Visually | Date chip; Duration; Source metadata; Stats |
| 89 | Breakout and Complementary Sections Uniquely Labelled | Aside; Related links; Supplemental panel |
| 90 | Comments, Panels, and Supplemental Regions Clearly Named | Comments region; Drawer; Supplemental panel; Share tools |
| 91 | All Interactive Elements Reachable by Keyboard | All interactive components |
| 92 | All Interactive Elements Operable by Keyboard | All interactive components |
| 93 | Standard Keyboard Activation Preserved | Button; Link; Checkbox; Radio; Menu item |
| 94 | No Keyboard Trap | Modal; Menu; Editor; Media player; Carousel |
| 95 | Focus Indicator Always Visible | All interactive components |
| 96 | Focus Indicator Not Suppressed Without Equivalent | All interactive components |
| 97 | Focus Order Logical Through Forms | Form; Wizard; Checkout |
| 98 | Focus Order Logical Through Navigation | Header nav; Sidebar nav; Breadcrumb; Pagination |
| 99 | Focus Does Not Move Unexpectedly During Input | Form; Combobox; OTP input |
| 100 | Focus Moves to New Context on Open | Modal; Dialog; Drawer; Popover |
| 101 | Focus Returns on Close | Modal; Dialog; Drawer; Popover; Info panel |
| 102 | Programmatic Focus Uses Appropriate Targets | Modal; Alert; Error summary; SPA route |
| 103 | Hidden Focusable Elements Revealed on Focus | Skip link; Off-canvas control; Hidden utility link |
| 104 | Positive Tabindex Avoided | All interactive components |
| 105 | Tabindex Zero Used Only on Intended Interactive Targets | Custom controls; Scroll regions; Panels |
| 106 | Tabindex Minus One Used for Programmatic Focus Only | Main target; Error summary; Dialog heading |
| 107 | Alternative Input Method Support | All interactive components |
| 108 | Gesture Functions Have Non-Gesture Alternatives | Carousel; Slider; Map; Reorder list; Drag/drop |
| 109 | Pointer Precision Not Required for Basic Tasks | Small icon buttons; Map controls; Dense menus |
| 110 | Target Size Meets Minimum Usability Threshold | Button; Link; Chip; Pagination; Toggle |
| 111 | Explicit Submit Control Present | Form; Comment form; Search form |
| 112 | Submission Occurs Only on Explicit Action | Form; Select; Filter bar |
| 113 | Required Fields Indicated Programmatically | Input; Select; Textarea; Checkbox group |
| 114 | Required Fields Indicated Visually | Input; Select; Textarea; Checkbox group |
| 115 | Optional Fields Marked Where Pattern Requires | Form field; Optional metadata |
| 116 | Input Format Expectations Communicated | Date input; Phone input; Password field; OTP |
| 117 | Appropriate Input Type Used | Email input; Tel input; Number input; Date input |
| 118 | Autocomplete Used for Personal Data Where Appropriate | Address form; Payment form; Profile form |
| 119 | Related Inputs Grouped Semantically | Fieldset; Address group; Payment group |
| 120 | Radio Groups Operate as One Logical Question | Radio group |
| 121 | Checkbox Sets Grouped Where They Share a Question | Checkbox group |
| 122 | Error Messages Shown When Submission Fails | Form; Comment form; Checkout |
| 123 | Error Messages Are Announced to Assistive Technology | Form; Error summary; Inline validation |
| 124 | Error Message Identifies the Relevant Field | Form field; Error summary |
| 125 | Error Message Explains the Problem | Form field; Error summary |
| 126 | Error Message Tells User How to Fix It | Form field; Error summary; Password field |
| 127 | Error Summary Provided for Multiple Errors | Long form; Checkout; Registration |
| 128 | Error Summary Supports Navigation to Fields | Error summary |
| 129 | User Input Preserved After Validation Failure | Form; Comment form; Checkout |
| 130 | Validation Does Not Interrupt Every Keystroke Inappropriately | Form field; Search field; Password field |
| 131 | Error Cues Persist Long Enough to Be Used | Toast; Inline validation; Error summary |
| 132 | Reset Buttons Avoided or Safe | Form; Settings form |
| 133 | Form Completion Possible by Keyboard Only | Entire form journey |
| 134 | Password and Complex Input Assistance Available | Password field; OTP; Security question |
| 135 | Submit Controls Not Inaccessibly Disabled | Submit button; Save button |
| 136 | Link Purpose Understandable in Isolation | Inline link; Card link; Footer link; Breadcrumb |
| 137 | Repeated Link Text Distinguishable Where Destinations Differ | Lists of links; Cards; Related links |
| 138 | Adjacent Duplicate Links Consolidated | Card; Teaser; Media promo |
| 139 | External Link Warning Included | External link; Footer link; CTA |
| 140 | Download or Alternate Format Links Identified | Download link; PDF link; App store link |
| 141 | Breadcrumbs Structured as Navigation List | Breadcrumb |
| 142 | Breadcrumb Current Page Is Not an Active Link | Breadcrumb |
| 143 | Navigation Menus Use Correct Structural Semantics | Global nav; Sidebar nav; Footer nav; Mega menu |
| 144 | Current Navigation State Programmatically Exposed | Tabs; Menu; Pagination; Breadcrumb; Filter |
| 145 | Search Region Identifiable | Search form; Search results header |
| 146 | Search Suggestions Announced Accessibly | Autocomplete; Search suggest; Typeahead |
| 147 | Share and Auxiliary Tool Clarity | Share tools; Save; Print; Overflow menu |
| 148 | SPA Route Changes Update Focus Position | SPA shell; Route container |
| 149 | SPA Route Changes Update History | SPA shell; Router |
| 150 | Route Change Loading State Communicated | SPA shell; Route loader; Skeleton |
| 151 | Status Messages Announced Without Forced Focus Change | Toast; Inline success; Status banner |
| 152 | Critical Alerts Perceivable in Multiple Modalities | Critical alert; System alert; Confirmation failure |
| 153 | Notifications Not Overbearing | Toast system; Notification center |
| 154 | Standard OS or Platform Notifications Used When Appropriate | Native notification bridge; App shell |
| 155 | Dynamic Content Discoverable After Update | Infinite list; Comments; Expand-on-load section |
| 156 | Focus Not Stolen by Non-Critical Updates | Toast; Autosave; Suggestion update |
| 157 | State Changes Reflected Programmatically | Disclosure; Checkbox; Toggle; Tabs; Tree; Accordion |
| 158 | State Change Announced When It Matters | Form submit; Save state; Toggle; Selection |
| 159 | Live Regions Used Appropriately | Toast; Status area; Search suggest |
| 160 | Update Timing Allows Perception | Toast; Status banner; Inline feedback |
| 161 | Disclosure Controls Expose Expanded State | Disclosure; Accordion; Details/summary; Filters panel |
| 162 | Disclosure Controls and Content Linked | Disclosure; Accordion; Filter panel |
| 163 | Collapsed Disclosure Content Removed Accessibly | Disclosure; Accordion; Filter panel |
| 164 | Revealed Content Follows Control Logically | Disclosure; Accordion; Filter panel |
| 165 | Accordion Items Use Heading + Button Pattern | Accordion |
| 166 | Single-Select Accordions Enforce One Open Item | Accordion |
| 167 | Tabs Use Correct Roles When Enhanced | Tabs |
| 168 | Tabs Preserve Non-JavaScript Access | Tabs |
| 169 | Only Active Tab Panel Exposed | Tabs |
| 170 | Information Panels Open and Close Predictably | Info panel; Drawer; Popover |
| 171 | Information Panels Not Used for Essential-Only Content | Info panel; Drawer; Popover |
| 172 | Modal Dialog Announces Identity and Modality | Modal; Alert dialog |
| 173 | Modal Dialog Blocks Background Interaction | Modal; Alert dialog |
| 174 | Modal Dialog Has Accessible Close Method | Modal; Alert dialog |
| 175 | Modal Dialog Content Fits or Scrolls | Modal; Alert dialog |
| 176 | Action Dialog Uses Buttons vs Links Appropriately | Modal; Confirmation dialog |
| 177 | Mega Menu Trigger Uses Button Semantics | Mega menu |
| 178 | Mega Menu Closes on Escape, Blur, or Outside Click | Mega menu |
| 179 | Carousel Is Entirely User Driven | Carousel |
| 180 | Carousel Hidden or Faint Items Not Presented as Fully Available | Carousel |
| 181 | Native Media Controls or Accessible Equivalent Present | Audio player; Video player |
| 182 | Media Does Not Autoplay Unexpectedly | Audio player; Video player; Promo media |
| 183 | Captions Available for Spoken Video | Video player |
| 184 | Audio Description or Equivalent for Essential Visual Information | Video player; Rich media |
| 185 | Promo Has One Clear Primary Action | Promo; Hero; Teaser |
| 186 | Promo Headline Consistent With Destination | Promo; Hero; Teaser |
| 187 | Promo Media Indicators Explained Non-Visually | Promo; Video teaser |
| 188 | Card Collections Use List Structure | Card collection; Search results; Promo grid |
| 189 | Card Headline Comes First in Source Order | Card; Promo card; Article teaser |
| 190 | Card Expandable Regions Follow Toggle State | Expandable card |
| 191 | Comment Stream Uses Nested Structure for Replies | Comment stream; Forum thread |
| 192 | Comment Submission Feedback Accessible | Comment form; Thread composer |
| 193 | Comment Controls Clearly Labelled | Comment actions; Reply; Vote; Share; Overflow |
| 194 | Character Limits Communicated During Comment Entry | Comment input; Textarea |
| 195 | Rating Displays Express Value in Text | Rating display; Review summary |
| 196 | Interactive Ratings Use Semantic Form Controls | Rating input |
| 197 | Time Limits Can Be Extended, Disabled, or Adjusted | Session timeout; Quiz; Purchase flow; Verification flow |
| 198 | Timeout Warning Issued Before Expiry | Session timeout; Purchase flow |
| 199 | Timeout Consequences Communicated | Session timeout; Purchase flow; Draft editor |
| 200 | Unexpected Context Changes Prevented | Form; Navigation; Select; SPA route; Search filter |
