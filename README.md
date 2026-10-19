# Vendor Proposal → Site-Card Deck Skill

Enterprise Claude Skill for Out-of-Home (OOH) media planning. Converts messy vendor proposals into billups branded site-card decks.

**Built for World's Largest Independent OOH Agency**

### Why this is not a parsing task
Vendor proposals have zero standard structure. One vendor uses tables, another bullets, another spreads 1 site across 4 slides. Regex breaks. This skill renders proposals to images and reads them like a human planner.

### Workflow
1.  **Render to images:** `pdftoppm -png -r 150` or `soffice --headless --convert-to pdf`
2.  **Extract real images:** `pdfimages` + filter <400px (logos), identify photo vs map screenshot
3.  **Build JSON:** 1 record per site (see `site_data_schema.md`)
4.  **Build deck:** `python3 scripts/build_deck.py sites.json billups_site_card_template_v2.pptx output.pptx`
5.  **QA:** Convert to PDF → render → visual check (price, photo/map swap, overflow)

### Brand Compliance
- Template: `billups_site_card_template_v2.pptx` ONLY
- Font: Manrope mandatory (per billups brand guidelines)
- Keep logo/footer/pin icons untouched

### Stack
`pdfimages, pdftoppm, python-pptx, soffice, Claude Read Tool`

### Use Case
Real client pricing - accuracy critical. Used for enterprise OOH campaign planning.
