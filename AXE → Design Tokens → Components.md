
# AXE → Design Tokens → Components (Unified Mapping)

| AXE Rule ID | Design Tokens Involved | Impacted Components / Patterns | Atomic Level | Rationale |
|---|---|---|---|---|
| color-contrast | color.foreground, color.background, color.state.*, opacity, elevation.overlay | Typography, Button, Link, Form fields, Alerts, Badges, Cards | Atom | Contrast is governed entirely by colour tokens and state tokens; all visual components inherit this dependency. |
| button-name | content.label, icon.semantic, aria.label | Button, Icon button, Toggle, FAB | Atom | Naming depends on content tokens and icon semantics; icons must not be relied on without text equivalents. |
| link-name | content.linkText, typography.linkStyle | Link, Navigation item, Breadcrumb, Card link | Atom / Molecule | Link meaning must be conveyed through content tokens; styling alone cannot provide meaning. |
| label | content.label, typography.label, spacing.form, color.text.secondary | Input, Select, Checkbox, Radio, Textarea | Atom | Labels rely on content + typography tokens; spacing ensures association clarity. |
| label-title-only | content.label.visible, typography.label | Form fields | Molecule | Token constraint: labels must be visible, not only programmatic. |
| input-image-alt | content.altText, icon.semantic | Image button, Icon button | Atom | Functional imagery depends on semantic content tokens. |
| image-alt | content.altText | Image, Card, Media | Atom / Molecule | Alt text is a content token dependency, not visual. |
| image-redundant-alt | content.altText, content.body | Image + text compositions | Molecule | Prevent duplication across content tokens. |
| aria-command-name | aria.label, content.label | Tabs, Menu, Accordion, Buttons | Molecule | Accessible names derive from semantic content tokens. |
| aria-input-field-name | aria.label, content.label | Custom input, Combobox | Molecule | Naming consistency across custom controls. |
| aria-dialog-name | aria.label, content.heading | Modal, Dialog | Organism | Dialog naming often tied to heading tokens. |
| aria-hidden-focus | focus.visibility, state.hidden, z-index.layering | Modal, Drawer, Tooltip, Hidden panels | Organism | Hidden state tokens must align with focus tokens to prevent exposure. |
| tabindex | focus.order, focus.visible, spacing.layout | All interactive components | Atom | Focus behaviour depends on system-level focus tokens and DOM order discipline. |
| skip-link | focus.visible, spacing.offset, z-index.overlay | Skip link component | Atom | Requires visibility and layering tokens to appear correctly on focus. |
| bypass | focus.management, layout.structure | Layout, Navigation shell | Template | Depends on structural tokens and focus movement logic. |
| heading-order | typography.heading.*, spacing.verticalRhythm | Page sections, Content blocks | Organism | Heading hierarchy driven by typography scale tokens. |
| empty-heading | typography.heading, content.heading | Heading component | Atom | Heading tokens must always include content. |
| document-title | content.title | Page template | Template | Title is a content token at page level. |
| html-has-lang | content.language | Global document | Template | Language is a system-level content token. |
| valid-lang | content.language.inline | Rich text, CMS content | Molecule | Inline language switching depends on content metadata tokens. |
| video-caption | media.caption, content.transcript | Video player | Organism | Captioning is a media/content token dependency. |
| no-autoplay-audio | motion.autoPlay, media.controls | Media player | Organism | Motion/audio behaviour governed by motion tokens. |
| meta-refresh | timing.autoRefresh | App shell, routing | Template | Timing tokens should not enforce forced refresh without control. |
| frame-title | content.title | Embedded iframe | Molecule | Naming of embedded content relies on content tokens. |
| definition-list | typography.body, spacing.definitionList | Definition list component | Molecule | Structured content depends on layout and typography tokens. |
| duplicate-id-aria | id.generation, component.instanceId | Forms, dynamic components | Molecule | Unique IDs often generated via system tokens/utilities. |
| aria-roles | semantic.roleMapping | Custom components | Molecule | Semantic mapping layer between tokens and DOM roles. |
| aria-required-attr | semantic.roleMapping, state.* | Composite widgets | Molecule | Required attributes often linked to state tokens. |
| aria-required-children | semantic.structure | Tabs, Menu, Tree | Molecule | Structural token relationships. |
| aria-required-parent | semantic.structure | Same as above | Molecule | Parent-child hierarchy enforced via component structure. |
| region | layout.landmarks, spacing.layout | Layout, Page shell | Template | Landmarks defined at layout token level. |
| landmark-one-main | layout.main | Page template | Template | Only one main region allowed per layout token definition. |
| page-has-heading-one | typography.heading.h1 | Page template | Template | Top-level heading enforced via typography tokens. |
| accesskeys | interaction.shortcut | Global interaction model | Template | Keyboard shortcut tokens (rarely recommended). |

# Bi-directional Mapping
A. Component → Required AXE Tests

| Component | Required AXE Tests | Token Dependencies |
|---|---|---|
| Button | button-name, color-contrast, tabindex | color.*, content.label, focus.* |
| Icon Button | button-name, input-image-alt, color-contrast, tabindex | icon.semantic, content.altText, color.*, focus.* |
| Link | link-name, color-contrast | content.linkText, color.* |
| Form Input | label, aria-input-field-name, tabindex | content.label, typography.label, focus.* |
| Checkbox / Radio | label, color-contrast, tabindex | content.label, color.*, focus.* |
| Select / Combobox | label, aria-input-field-name, aria-required-attr, tabindex | content.label, semantic.roleMapping |
| Modal / Dialog | aria-dialog-name, aria-hidden-focus, tabindex | aria.label, focus.*, z-index.* |
| Tabs | aria-required-children, aria-roles, aria-command-name | semantic.structure, aria.label |
| Menu | aria-roles, aria-required-children, aria-command-name | semantic.structure |
| Card | image-alt, link-name, color-contrast | content.altText, content.linkText, color.* |
| Image | image-alt | content.altText |
| Video Player | video-caption, no-autoplay-audio | media.caption, motion.* |
| Table | empty-table-header, definition-list (if used), color-contrast | typography.*, spacing.* |
| Heading | empty-heading, heading-order | typography.heading.* |
| Layout / Page Template | bypass, skip-link, region, document-title, page-has-heading-one | layout.*, content.title |
| Navigation | link-name, bypass, skip-link | content.linkText, focus.* |

B. Test → Impacted Components

This defines where each AXE test should be applied across the system.

| AXE Test | Impacted Components |
|---|---|
| image-alt | Image, Card, Media block |
| input-image-alt | Icon button, Image button |
| button-name | Button, Icon button, Toggle |
| link-name | Link, Navigation, Card |
| label | All form controls |
| aria-command-name | Tabs, Menu, Accordion |
| aria-input-field-name | Combobox, Custom input |
| aria-dialog-name | Modal, Dialog |
| aria-hidden-focus | Modal, Drawer, Tooltip |
| tabindex | All interactive components |
| skip-link | Skip link |
| bypass | Layout, Navigation |
| color-contrast | All visual components |
| heading-order | Page sections, Content layouts |
| empty-heading | Heading |
| document-title | Page template |
| html-has-lang | Document root |
| valid-lang | Rich text |
| video-caption | Video player |
| no-autoplay-audio | Media components |
| meta-refresh | App shell |
| frame-title | Embedded iframe |
| definition-list | Definition list component |
| duplicate-id-aria | Forms, dynamic UI |
| aria-roles | Custom components |
| aria-required-attr | Composite widgets |
| aria-required-children | Tabs, Menu, Tree |
| aria-required-parent | Tabs, Menu, Tree |
| region | Layout |
| landmark-one-main | Layout |
| page-has-heading-one | Page template |
