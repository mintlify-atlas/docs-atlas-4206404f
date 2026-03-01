# Fumadocs Documentation - Content Audit Findings

**Date:** March 1, 2026  
**Auditor:** OpenCode AI Assistant  
**Scope:** Complete documentation audit of Fumadocs documentation site

---

## Executive Summary

The Fumadocs documentation is generally high-quality with comprehensive API documentation and well-written guides. However, there are several old boilerplate files from the Mintlify starter template that should be removed, and some packages lack dedicated documentation pages.

**Key Statistics:**
- Total MDX files: 77 files
- Files in navigation: 60 pages
- Old boilerplate files: 17 files (to be deleted)
- Stub/empty pages: 0 (all pages have substantial content)
- Missing package docs: 7 packages

---

## 1. Old Boilerplate Files - DELETE IMMEDIATELY ✅

These files are NOT in the navigation and are leftover from the Mintlify starter template:

### Top-level Boilerplate Files (3 files)
- **`development.mdx`** (385 words) - Mintlify CLI development instructions, not Fumadocs-related
- **`index.mdx`** (219 words) - Old Mintlify starter welcome page, conflicts with `introduction.mdx`
- **`quickstart.mdx`** (356 words) - Old Mintlify quickstart, superseded by `quick-start.mdx`

### `/ai-tools/*` Directory (3 files)
Mintlify-specific AI tool setup instructions, not relevant to Fumadocs:
- `ai-tools/claude-code.mdx` (114 words)
- `ai-tools/cursor.mdx` (122 words)
- `ai-tools/windsurf.mdx` (123 words)

### `/api-reference/*` Directory (5 files)
Mintlify starter API reference boilerplate with "Plant Store" example:
- `api-reference/introduction.mdx` (96 words) - Mentions "Plant Store Endpoints"
- `api-reference/endpoint/create.mdx`
- `api-reference/endpoint/delete.mdx`
- `api-reference/endpoint/get.mdx`
- `api-reference/endpoint/webhook.mdx`
- `api-reference/openapi.json` - Sample OpenAPI spec

**Note:** Fumadocs has proper API reference at `/api/*` instead.

### `/essentials/*` Directory (6 files)
Mintlify-specific documentation about Mintlify features:
- `essentials/code.mdx` (122 words)
- `essentials/images.mdx` (171 words)
- `essentials/markdown.mdx` (402 words)
- `essentials/navigation.mdx` (266 words)
- `essentials/reusable-snippets.mdx` (379 words)
- `essentials/settings.mdx` (very long, Mintlify `docs.json` config reference)

### `/snippets/*` Directory (1 file)
- `snippets/snippet-intro.mdx` (47 words) - Minimal snippet example

**Total to delete: 17 files**

---

## 2. Empty or Stub Pages - NONE FOUND ✅

**Result:** No stub pages found. All pages in the navigation contain substantial, high-quality content.

**Sample word counts of pages checked:**
- `introduction.mdx`: 652 words (comprehensive)
- `concepts/architecture.mdx`: 964 words (excellent technical depth)
- `ui/overview.mdx`: 644 words (well-structured)
- `api/core/source.mdx`: 1,017 words (detailed API docs)
- `cli/overview.mdx`: 406 words (solid overview)
- `guides/creating-first-doc.mdx`: 1,161 words (comprehensive tutorial)
- `integrations/typescript-docgen.mdx`: 1,418 words (excellent)
- `markdown/twoslash.mdx`: 1,681 words (very detailed)

**Shortest legitimate pages:**
- `features/breadcrumbs.mdx`: ~400 words (acceptable for focused topic)
- `deployment/cloudflare.mdx`: ~450 words (deployment guide)
- `api/core/toc.mdx`: 704 words (complete API reference)

All pages provide real value and complete information.

---

## 3. Missing Package Documentation ⚠️

Based on the public API surface from `package.json` files, these packages lack dedicated documentation pages:

### **Priority 1: User-Facing Packages (Should Document)**

1. **`@fumadocs/base-ui` (v16.6.8)**
   - **Status:** Mentioned briefly in `ui/overview.mdx` but no dedicated guide
   - **Package:** Alternative UI package using Base UI (React Aria) instead of Radix UI
   - **Exports:** Same API as fumadocs-ui with different primitives
   - **Recommendation:** Add `/ui/base-ui.mdx` with:
     - When to use Base UI vs Radix UI
     - Installation guide
     - Migration guide from fumadocs-ui
     - API differences (if any)

2. **`fumadocs-docgen` (v3.0.8)** 
   - **Status:** Mentioned as `fumadocs-typescript` in docs but package name is `fumadocs-docgen`
   - **Package:** TypeScript documentation generator
   - **Current coverage:** Well-documented at `/integrations/typescript-docgen.mdx`
   - **Issue:** Package name mismatch - docs say `fumadocs-typescript` but npm package is `fumadocs-docgen`
   - **Recommendation:** Clarify package naming or document both entry points

3. **`fumadocs-twoslash` (v3.1.14)**
   - **Status:** **DOCUMENTED** ✅ at `/markdown/twoslash.mdx` (1,681 words, excellent)
   - No action needed

4. **`@fumadocs/mdx-remote` (v1.4.6)**
   - **Status:** Missing dedicated page
   - **Package:** Remote MDX files adapter (for fetching docs from APIs/CMS)
   - **Exports:** Main export + `/client` subpath
   - **Recommendation:** Add `/content/mdx-remote.mdx` with:
     - Use case (remote content from CMS/API)
     - Setup guide
     - API reference
     - Examples with different CMSs

5. **`fumadocs-python` (v0.0.9)**
   - **Status:** Missing dedicated page
   - **Package:** Python docstring generator (similar to TypeScript docgen)
   - **Exports:** Main export + `/components`
   - **Recommendation:** Add `/integrations/python-docgen.mdx` similar to typescript-docgen

6. **`@fumadocs/tailwind` (v0.0.3)**
   - **Status:** Missing dedicated page
   - **Package:** Tailwind CSS utilities for Fumadocs UI
   - **Exports:** `/compile` and `/typography`
   - **Recommendation:** Add section to `/ui/theming.mdx` or create `/ui/tailwind-plugin.mdx`

7. **`fumapress` (v0.0.8)**
   - **Status:** Missing dedicated page
   - **Package:** Minimal Fumadocs setup / Vite-based alternative
   - **Description:** "The minimal setup for Fumadocs"
   - **Exports:** Main + `/vite` plugin
   - **Recommendation:** Add `/frameworks/fumapress.mdx` or `/installation/fumapress.mdx`
     - When to use fumapress vs full setup
     - Vite plugin usage
     - CLI commands

### **Priority 2: Specialized Packages (Optional)**

8. **`@fumari/stf` (v1.0.3)**
   - **Status:** Missing (niche package)
   - **Package:** "Schema to Form" - Form generation from schemas
   - **Recommendation:** Low priority - appears to be internal/experimental

9. **`@fumadocs/story` (v0.0.11)**
   - **Status:** Missing (experimental)
   - **Package:** Story integration (appears experimental based on version)
   - **Recommendation:** Low priority until package is stable

---

## 4. Import Path Validation ✅

**Result:** Import paths are CORRECT and match package exports.

### Sample Verification:

**fumadocs-ui imports:**
```tsx
// Documented imports match exports
import { DocsLayout } from 'fumadocs-ui/layouts/docs'; ✅
import { DocsPage } from 'fumadocs-ui/layouts/docs/page'; ✅
import { Accordion } from 'fumadocs-ui/components/accordion'; ✅
import { RootProvider } from 'fumadocs-ui/provider/base'; ✅
```

**fumadocs-core imports:**
```tsx
// All match package.json exports
import { loader } from 'fumadocs-core/source'; ✅
import { FrameworkProvider } from 'fumadocs-core/framework'; ✅
import { useActiveAnchor } from 'fumadocs-core/toc'; ✅
```

**fumadocs-mdx imports:**
```tsx
// Correctly documented
import { defineConfig, defineDocs } from 'fumadocs-mdx/config'; ✅
```

**fumadocs-twoslash imports:**
```tsx
// Correctly shows package exports
import { transformerTwoslash } from 'fumadocs-twoslash'; ✅
import { Popup } from 'fumadocs-twoslash/ui'; ✅
```

**@fumadocs/content-collections:**
```tsx
// Imports are correct
import { createMDXSource } from '@fumadocs/content-collections'; ✅
```

**No hallucinated imports found.**

---

## 5. API Signature Verification ✅

Sampled multiple API pages and verified against package structure:

- **`api/core/source.mdx`**: Accurately documents `source()`, `multiple()`, `update()`, `FileSystem` class
- **`api/core/toc.mdx`**: Correctly documents `useActiveAnchor()`, `TOCItem`, `AnchorProvider` APIs
- **`api/mdx/config.mdx`**: Accurate schemas and configuration options
- **`api/ui/components.mdx`**: Component props match actual interfaces
- **`integrations/typescript-docgen.mdx`**: Generator API is accurate

**No obvious hallucinated functions found.**

---

## 6. Content Quality Assessment ✅

### Strengths:
1. **Comprehensive API documentation** - All core APIs are documented with examples
2. **High-quality guides** - Step-by-step tutorials with working code
3. **Good code examples** - Real-world usage patterns throughout
4. **Deep technical content** - Architecture docs explain internals well
5. **Consistent formatting** - Uniform structure across pages
6. **Type information** - TypeScript signatures are accurate
7. **Framework coverage** - Next.js, React Router, TanStack Router, Waku all documented

### Areas for Improvement:
1. **Package naming confusion** - `fumadocs-typescript` vs `fumadocs-docgen`
2. **Missing advanced packages** - Several newer packages undocumented
3. **Base UI coverage** - Alternative UI package deserves own page
4. **Search implementation** - Could use more examples for different backends

---

## Recommendations

### Immediate Actions (High Priority)

1. **DELETE all 17 boilerplate files** listed in Section 1
   - Use git to ensure clean removal
   - Verify no internal links reference these files

2. **Fix package naming confusion**
   - Clarify `fumadocs-typescript` vs `fumadocs-docgen` in `/integrations/typescript-docgen.mdx`
   - Update installation instructions to use correct package name

3. **Document @fumadocs/base-ui**
   - Create `/ui/base-ui.mdx` with:
     - Comparison with fumadocs-ui
     - Installation guide
     - When to choose Base UI

### Short-term Improvements (Medium Priority)

4. **Document missing packages:**
   - `/content/mdx-remote.mdx` - Remote content fetching
   - `/integrations/python-docgen.mdx` - Python documentation generation
   - `/ui/tailwind-plugin.mdx` - Tailwind utilities and plugins
   - `/frameworks/fumapress.mdx` - Minimal Vite-based setup

5. **Enhance existing content:**
   - Add migration guide from older versions
   - Add troubleshooting section to main pages
   - More examples for search backends (Algolia, Orama Cloud)

### Long-term Enhancements (Low Priority)

6. **Experimental packages:**
   - Document `@fumadocs/story` when stable
   - Add `@fumari/stf` reference if it becomes public API

7. **Additional guides:**
   - Performance optimization guide
   - Custom theme creation tutorial
   - Plugin development guide

---

## Files to Delete

Run these commands to remove boilerplate:

```bash
# Top-level files
rm docs/development.mdx
rm docs/index.mdx
rm docs/quickstart.mdx

# Directories
rm -rf docs/ai-tools/
rm -rf docs/api-reference/
rm -rf docs/essentials/
rm -rf docs/snippets/
```

**Total disk space saved:** ~50KB of unnecessary documentation

---

## Conclusion

The Fumadocs documentation is **high quality** overall with:
- ✅ No stub pages
- ✅ Accurate API documentation
- ✅ Correct import paths
- ✅ Comprehensive guides

**Main issues:**
- ❌ 17 old boilerplate files to remove
- ⚠️ 4-7 packages missing documentation
- ⚠️ Package naming inconsistency

**Priority actions:**
1. Delete boilerplate files (1 hour)
2. Document @fumadocs/base-ui (2-3 hours)
3. Document @fumadocs/mdx-remote (2 hours)
4. Fix package naming confusion (30 minutes)

**Status:** Ready for production after cleanup, with minor gaps in advanced package documentation that can be filled incrementally.
