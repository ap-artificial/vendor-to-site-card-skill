Vendor Proposal → Site-Card Deck Skill
Enterprise Claude Skill for Out-of-Home (OOH) media planning. Converts messy vendor proposals into agency-branded site-card decks.
Built for Enterprise OOH Agency Workflow

Why this is not a parsing task
Vendor proposals have zero standard structure. One vendor uses tables, another bullets, another spreads 1 site across 4 slides. Regex breaks. This skill renders proposals to images and reads them like a human planner.

Workflow
Render to images: pdftoppm -png -r 150 or soffice --headless --convert-to pdf
Extract real images: pdfimages + filter <400px (logos), identify photo vs map screenshot
Build JSON: 1 record per site (see site_data_schema.md)
Build deck: python3 scripts/build_deck.py sites.json agency_site_card_template.pptx output.pptx
QA: Convert to PDF → render → visual check (price, photo/map swap, overflow)

Brand Compliance
Template: Use client's agency master template (do not commit proprietary .potx)
Font: Manrope or client brand font (enforce via brand guidelines)
Keep logo/footer/pin icons untouched - use placeholder if needed

Stack
pdfimages, pdftoppm, python-pptx, soffice, Claude Read Tool

Use Case
Real client pricing - accuracy critical. Used for enterprise OOH campaign planning. No client data included.
