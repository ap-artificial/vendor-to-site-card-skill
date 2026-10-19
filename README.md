# Vendor Proposal → Site-Card Deck Skill

Enterprise Claude Skill for OOH media planning. Converts messy vendor proposals into agency-branded site-card decks.

Built for enterprise OOH workflow.

Workflow:
1. Render proposals to images
2. Extract real images (filter <400px logos)
3. Build JSON (1 record per site)
4. Build deck via python-pptx
5. QA visual check

Brand Compliance:
- Use client master template (no proprietary file committed)
- Manrope / client brand font
- No client data included

Stack: pdfimages, pdftoppm, python-pptx, soffice, Claude Read Tool
