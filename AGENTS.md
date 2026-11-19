# AGENTS.md

## Language and formatting

- Write code identifiers, comments, test names, and assertion messages in English. Maintain the GDD in Russian and
  player-facing copy in localization resources.
- Use tabs with a width of four in C#. Declare locals with explicit types. Separate logical blocks with blank lines and
  limit formatting edits to touched code.
- Use a concise English Git commit title only, without a body, trailers, or attribution.

## Design source of truth

- [docs/GDD.md](docs/GDD.md) defines the design, milestones, and implementation status. Record changes to gameplay rules
  or scope there before implementing them.
- Preserve the core experience of hiring, furnishing a visible office, and growing a software business. Build RD
  Corporation's identity around reusable product modules, client commitments, and room workflows. Create original
  content, layouts, characters, visuals, and audio.
- Treat numerical values in the GDD as initial balance targets. Record meaningful adjustments and the playtest results
  that motivated them.

## Unity structure and shared modules

- Put new project-owned content under `Assets/_Project`. Follow the responsibilities in the GDD when adding folders and
  assemblies.
- `Assets/TemplateSources` contains Windows junctions into the sibling UnityTemplates checkout. Changes through them
  affect the shared checkout. Keep game rules and project-specific adapters in `Assets/_Project`.
- Review the UnityTemplates module and its dependencies before adding it. Extend `Tools/Link-UnityTemplates.ps1` with
  the required source units and keep the linked folder metadata in Git. Use `Tools/UnityTemplates.revision` to record
  the shared revision verified with this project. See [README.md](README.md) for bootstrap instructions.

## Simulation guardrails

- Keep economy, contracts, placement, and offline progression in pure C# under `Assets/_Project/Runtime/Core`.
  GameObjects, animation, input, and panels present state through the application layer.
- Use one advancement path for foreground and offline time. Cover event boundaries, long absences, save reloads,
  duplicate settlements, clock rollback, and recovery from an empty treasury.
- Keep money, IDs, clocks, and seeded randomness explicit. Validate purchases and assignments before changing state.
  Store only stable IDs and serializable state in saves.
- Verify affected gameplay in the Unity Editor. Use EditMode tests for simulation rules and PlayMode checks for scene
  and UI wiring once those systems exist.