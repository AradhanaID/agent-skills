# Reference — structure

The authoritative placement rules. Conventions stated anywhere else are near-places of this file; correct them here, not at the use site.

## Context pointer

These rules are placeholders until the repo's layout is judged. Replace them with the real values in place — do not append a parallel section.

## Placement rules

```
src/
  components/   one folder per component, with test, story, styles colocated
  hooks/        one file per hook, test colocated
  pages|routes/ one folder per route in the router
  lib/          pure utilities, no react imports
  assets/       static files referenced via import only
  types/        shared type definitions
```

- **One home per file.** A file is placed by its primary kind, imported from there; no copy-referencing.
- **Colocation wins over centralizing.** A test or style used by one component lives next to it, not in a global folder.
- **The route folder owns fetch code.** Data-fetching helpers belong to the route folder that uses them, not to a catch-all api folder, until two routes share the exact helper.

## Naming

- Components and hooks: PascalCase files for components, `useX` for hooks.
- Plurality follows the content — `components/` holds many, a single feature's folder is singular.
- No `utils.ts` grown into a second home for anything with a real name.
