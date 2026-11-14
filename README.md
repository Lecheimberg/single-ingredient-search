# Single Ingredient Search – Backend

**Endpoint:** `GET /api/search?ingredient=chicken`

Returns recipes that contain the given ingredient:

```json
{ "ingredient": "chicken", "count": 2, "results": [
  { "id": "52795", "title": "Chicken Handi", "image": "https://...jpg", "source": "themealdb" }
]}
```

## Files
- `app/api/search/route.ts` – Next.js App Router route. Validates input (400 if missing or > 50 chars), returns 502 if the recipe API fails.
- `lib/recipes/searchByIngredient.ts` – Calls TheMealDB (free, no API key). Normalizes input ("Chicken Breast" -> `chicken_breast`). Results cached for 1 hour.

## How to add to the project
1. Copy both files to the same paths (inside `src/` if the project uses it). Uses the default `@/` import alias.
2. `npm run dev` and open `http://localhost:3000/api/search?ingredient=chicken`.

## Swapping the API
If we choose a different recipe API, only `lib/recipes/searchByIngredient.ts` changes. Optional: set `RECIPE_API_BASE_URL` in `.env.local`.
