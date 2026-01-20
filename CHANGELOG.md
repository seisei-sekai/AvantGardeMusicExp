# Changelog

All notable changes to this repository are documented in this file.

## [1.0.0] - 2026-01-20

### Added - Initial Release

#### Website Migration
- Complete static mirror of [shichengzhang.web.illinois.edu](https://shichengzhang.web.illinois.edu/)
- Downloaded all pages, assets, images, and media files using `wget`
- Preserved original WordPress structure and functionality

#### Documentation
- **README.md** - Comprehensive repository documentation including:
  - About section with Benny Zhang's mission statement
  - Website sections overview
  - Highlighted works catalog
  - Repository structure
  - Local development instructions
  - GitHub Pages deployment guide
  - CV download link
  - Credits and license information

- **SITEMAP.md** - Complete navigation structure including:
  - Main navigation pages (Home, Projects, Music, Photography, Blog, About/CV)
  - All 4 music categories with direct links
  - 11+ featured projects and compositions
  - Media assets inventory
  - Technical information
  - External links and API endpoints

- **CHANGELOG.md** - This file documenting repository changes

#### Configuration Files
- **.gitignore** - Git ignore rules for:
  - macOS system files (.DS_Store, etc.)
  - Editor files (.vscode, .idea, etc.)
  - Temporary files
  - WordPress configuration files
  - Build tools

#### Content Structure

##### Main Pages
- `index.html` - Homepage with featured works
- `projects/` - Research & software projects
- `music-2/` - Music compositions overview
- `photography/` - Photography portfolio
- `blog-2/` - Blog section
- `about-2/` - Biography and CV

##### Featured Projects (11 directories)
- `ac-love/` - Love composition (2021)
- `ac-musica/` - Musica chorale generator (2021)
- `ac-melody-mutator/` - Melody transformation system
- `ac-octatonics/` - Octatonic scale explorations
- `ec-mutant/` - Mutant composition (2021)
- `ec-evolved/` - Evolved composition (2021)
- `ec-alien-abduction/` - Alien Abduction project
- `instrumental-ukiyo-e浮世绘/` - Ukiyo-e composition (2019)
- `sonification-epilepsy-harmonization/` - EEG research project
- `music-academics/` - Academic music collection
- `music-etudes/` - Music production practice
- `music-performances/` - Performance recordings
- `music-pop-music/` - Popular music works

##### Assets & Media
- `wp-content/themes/foliopress/` - Complete theme files
  - Bootstrap 4.0.0 CSS and JavaScript
  - Font Awesome 4.7 icon fonts
  - Custom theme styles and scripts
  
- `wp-content/uploads/2021/` - Media files organized by month
  - May: 99 JPEG images
  - October: 114 PNG images, 40 JPG images, 15 MP3 audio files
  - November: CV PDF (Benny_CV_11.pdf)

- `wp-content/plugins/jetpack/` - Jetpack plugin assets

- `wp-includes/` - WordPress core JavaScript libraries
  - jQuery 3.7.1
  - jQuery Migrate 3.4.1

##### Technical Files
- `robots.txt` - Search engine crawler directives
- `feed/` - RSS feed XML files
- `wp-json/` - WordPress REST API endpoints
- Multiple `index.html?p=XXX.html` files - WordPress permalink variants

### Technical Details

#### Migration Method
```bash
wget --no-check-certificate \
     --mirror \
     --convert-links \
     --adjust-extension \
     --page-requisites \
     --no-parent \
     https://shichengzhang.web.illinois.edu/
```

#### Technologies Preserved
- WordPress 6.9
- Foliopress Theme by Theme Horse
- Bootstrap 4.0.0
- Font Awesome 4.7
- Google Fonts (Poppins family)
- Jetpack plugin

#### Statistics
- **Total Directories:** 45+ directories at root level
- **Total Images:** 250+ image files (JPEG, PNG)
- **Audio Files:** 15+ MP3 files
- **Total Pages:** 20+ HTML pages including variants
- **Document Size:** ~100MB total

### Repository Setup
- Initialized Git repository structure
- Created comprehensive documentation
- Configured .gitignore for clean version control
- Ready for GitHub Pages deployment

### Future Enhancements (Planned)
- [ ] Optimize images for web (compression)
- [ ] Create mobile-responsive improvements
- [ ] Add search functionality
- [ ] Create custom 404 page
- [ ] Add Google Analytics integration
- [ ] Implement dark/light theme toggle
- [ ] Add print-friendly CV stylesheet
- [ ] Create project filtering system
- [ ] Add music player interface
- [ ] Implement lazy loading for images

## Notes

### Known Issues
- Some links use WordPress query string format (`index.html?p=XXX.html`) due to permalink structure
- Links are relative and converted for static hosting
- Some WordPress dynamic features (search, comments) are non-functional in static version

### Compatibility
- Works on all modern browsers (Chrome, Firefox, Safari, Edge)
- Responsive design supports mobile, tablet, and desktop
- No server-side processing required
- Can be hosted on any static file server

### Maintenance
This is a static snapshot taken on January 20, 2026. To update:
1. Re-run wget command on source website
2. Review and merge changes
3. Update this changelog
4. Commit and push to GitHub

---

**Created by:** Cursor AI Assistant  
**Date:** January 20, 2026  
**Source:** https://shichengzhang.web.illinois.edu/  
**Owner:** Benny Zhang (张世成)

