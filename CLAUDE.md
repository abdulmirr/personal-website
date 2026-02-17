# Website Design Recreation

## Workflow
When the user provides a reference image (screenshot) and optionally some CSS classes or style notes:

1. **Generate** a single `index.html` file using Tailwind CSS (via CDN). Include all content inline - no external files unless requested.

2. **Screenshot** the rendered page using Puppeteer (`npx puppeteer screenshot index.html --fullpage` or equivalent). If the page has distinct sections, capture those individually too.

3. **Compare** your screenshot against the reference image. Check for mismatches in:
   - Spacing and padding (measure in px)
   - Font sizes, weights, and line heights
   - Colors (exact hex values)
   - Alignment and positioning
   - Border radii, shadows, and effects
   - Responsive behavior
   - Image/icon sizing and placement

4. **Fix** every mismatch found. Edit the HTML/Tailwind code.

5. **Re-screenshot** and compare again.

6. **Repeat** steps 3-5 until the result is within ~2-3px of the reference everywhere.

Do NOT stop after one pass. Always do at least 2 comparison rounds. Only stop when the user says so or when no visible differences remain.

## Technical Defaults

- Use Tailwind CSS via CDN: `<script src="https://cdn.tailwindcss.com"></script>`
- Use placeholder images from https://placehold.co/ when source images aren't provided
- Mobile-first responsive design
- Single `index.html` file unless the user requests otherwise

## Best Practices

- **Exact measurements**: Use the reference image dimensions to calculate precise spacing values
- **Typography matching**: Pay special attention to font-family, size, weight, letter-spacing, and line-height
- **Color precision**: Extract exact hex/RGB values from the reference when possible
- **Component structure**: Use semantic HTML and appropriate Tailwind utility classes
- **Accessibility**: Include proper alt text, ARIA labels, and semantic markup
- **Icons**: Use Heroicons (via CDN) or inline SVG for icons when visible in reference

## Comparison Tools

- Use image diff tools or visual inspection to identify pixel-perfect differences
- Measure spacing with browser DevTools or screenshot analysis
- Document what was changed between iterations
- Call out any assumptions made when reference is ambiguous

## Output Format

After each iteration, provide:
1. Screenshot of current implementation
2. List of differences found vs. reference
3. Changes made to fix those differences
4. Confirmation whether another iteration is needed

## Edge Cases

- If fonts in reference aren't web-safe, use closest Google Fonts alternative
- If images are unclear, describe what's being used as placeholder
- If interactive elements are shown, implement basic hover/active states
- If animations are implied, add subtle Tailwind transitions

## Stopping Criteria

Continue iterating until:
- Visual differences are ≤2-3px across all sections
- Colors match within 5% tolerance (or exact if provided)
- Typography is visually indistinguishable
- User explicitly approves the result
