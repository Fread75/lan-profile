# CV + Cover Letter Generation System

## Overview
Automated generation of tailored job application materials (CV + cover letter) based on job postings while maintaining candidate authenticity.

## Core Principles
- **NEVER LIE OR INVENT** information about the candidate
- **KEEP AUTHENTIC VOICE** - candidate is not native English speaker, use simple, clear language
- **SUBTLE SPECIALIZATION** - highlight relevant experience without fabrication
- **CONCISE COMMUNICATION** - candidate prefers shorter, direct content

## Input Sources

### Candidate Context
- `context/cover_letter.txt` → Example cover letter for tone/style reference (if available)
- `context/portfolio.txt` → Portfolio extract for experience details (if available)
- `latex/cv.tex` → Master CV template (DO NOT MODIFY)
- `latex/cover_letter_template.tex` → Cover letter template

### Job Information
- Job posting URL
- Extract: job title, company, requirements, responsibilities, salary, location

## Output Requirements

### Directory Structure
```
out/YYYYMMDD/HHmm_[company_name]/
├── cover_lan_nguyen.tex
├── cover_lan_nguyen.pdf
├── cv_lan_nguyen.tex
└── cv_lan_nguyen.pdf
```

### Cover Letter Specifications
- **Length**: 70% of standard cover letter (3-4 paragraphs max)
- **Language Level**: Simple, clear, non-native English appropriate
- **Structure**: 
  1. Interest in position + company mission alignment
  2. Relevant experience with specific examples
  3. What interests candidate about the role
  4. Closing with value proposition
- **Remove** "Attached CV" references
- **No** overly complex vocabulary or extensive writing
- **No** typical AI phrasing

### CV Specifications
- **Base**: Copy original `latex/cv.tex` exactly
- **Only Change**: Position title to match target role appropriately
- **Subtle Highlighting**: Reframe existing experience bullets to emphasize relevant aspects
- **Education/Skills**: Keep as-is
- **Languages**: Include multilingual capabilities as strength

## Specialization Guidelines

### Position Title Updates
- **Social Media roles** → "Social Media Manager"
- **Content roles** → "Content Strategist" or "Digital Content Producer"
- **Account Management** → "Senior Account Manager"
- **Entry-level** → Match exact role title if appropriate

### Experience Reframing (Examples)
**Original**: "Managed social media platforms"
**For Partnerships role**: "Built partnerships with external content creators"
**For Content role**: "Developed content strategies across multiple channels"

### Skills Emphasis
- **Highlight relevant tools** mentioned in job posting
- **Emphasize measurable results** (80% traffic increase, 50 new contacts, etc., results can be over-exagerated, just a bit)
- **Show cross-functional collaboration** experience
- **Demonstrate international/multicultural work** when relevant

## Process Workflow

0. **Tech**: check machine time to get current time
1. **Job Analysis**: Extract key requirements, responsibilities, company culture
2. **Content Planning**: Identify relevant candidate experience to highlight
3. **Directory Creation**: out/YYYYMMDD/HHmm_[company]
4. **Document Generation**:
   - Cover letter with appropriate tone and length
   - CV with updated title and subtle emphasis shifts
5. **PDF Compilation**: `pdflatex` for both documents
6. **Cleanup**: Remove auxiliary LaTeX files

## Quality Checks

### Before Submission
- [ ] No fabricated information
- [ ] Simple, clear language appropriate for non-native speaker
- [ ] Cover letter under 4 paragraphs
- [ ] Job-specific keywords naturally integrated
- [ ] Measurable achievements included (exageration, just a bit, is ok)
- [ ] Professional but authentic tone maintained

### Common Pitfalls to Avoid
- **Don't** use overly sophisticated vocabulary
- **Don't** create experience that doesn't exist
- **Don't** make cover letter too long or elaborate
- **Don't** change fundamental CV structure
- **Don't** forget to update position title appropriately
- **Don't** leave auxiliary LaTeX files in output

## Technical Notes

### LaTeX Compilation
```bash
cd out/YYYYMMDD/HHmm_[company]
pdflatex cover_letter_lan_nguyen.tex
pdflatex cv_lan_nguyen.tex
rm -f *.aux *.log *.out *.synctex.gz *.fdb_latexmk *.fls
```

### File Management
- Keep original files unchanged
- Generate fresh documents for each application
- Use consistent naming convention
- Clean up build artifacts

## Success Metrics
- **Authenticity**: All information verifiable from candidate's actual experience
- **Relevance**: Clear connection between candidate skills and job requirements
- **Readability**: Appropriate language level maintained
- **Completeness**: All required documents generated and properly formatted
- **Quality**: review all, quality should be such as the candidate will be among 10% of best candidates

## Final review to user
- Give the path of the output to user
- Give a user a percentage of adequation of the job with user's profile
- Tell the user if he objectively is not a good fit for the job

---

*This system balances professional presentation with authentic candidate representation, ensuring truthful but effectively positioned applications.*