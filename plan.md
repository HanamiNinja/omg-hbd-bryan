# OMG Happy Birthday - Implementation Plan

## Project Overview
A static website generator for emergency birthday or small celebration. Surprises when you totally forgot it in a matter of few minutes. The system automates the creation of an interactive, personalized page that can be quickly deployed to GitHub Pages.

## Technology Stack
- **Framework**: User selectable via `config.md` (Options: Astro, Next.js, Static HTML)

## Data Structure

### `config.md` (Tech Stack)
```yaml
---
stack: "astro" # options: astro, nextjs, html
version: "latest"
---
```

### `data.md` (Content)
```yaml
---
name: "Bryan"
age: 30 # optional
language: "en" # options: en, es, fr, de, pt, it, ja, zh, etc.
favoriteAnimal: "cat" # options: cat, dog, or custom
primaryColor: "#FF6B9D"
secondaryColor: "#C44569"
customMessage: "I wish you the best of the best"
fromName: "Your Friend"
countryCode: "US" # for national anthem (optional)
celebrationSongUrl: "" # optional YouTube URL
---
```

## Implementation Workplan

### Phase 1: Project Setup & Scaffolding
- [ ] Create `config.md` to define technology stack
- [ ] Create scaffolding script/workflow that reads `config.md`:
  - If `astro`: Initialize Astro project
  - If `nextjs`: Initialize Next.js project
  - If `html`: Setup basic HTML/CSS/JS structure
- [ ] Configure GitHub Pages deployment based on selected stack
- [ ] Create basic project structure (components, layouts, pages) adapted to chosen stack
- [ ] Set up Tabler Icons integration
- [ ] Set up simple i18n system:
  - Create translation files for supported languages
  - Load ONLY the language specified in `data.md`
  - Fallback to English if language not available
  - Set HTML `lang` attribute based on selected language
- [ ] Create `.gitignore` and initial `README.md`

### Phase 2: Name Entry Screen (Mobile-First)
- [ ] Create clean form layout with mostly white background, almost-black text
- [ ] Implement letter hint input fields (e.g., "B _ _ _ _ N")
  - Individual rounded input boxes for each letter
  - Show first and last letter as hints
  - Auto-focus on first empty field
  - Auto-advance to next field on input
- [ ] Add name validation logic
  - Compare entered name with `data.md` configuration
  - Show localized "Not cool enough" alert on mismatch
  - Trigger loading screen on correct name
- [ ] Add localized text:
  - "We are looking for a super special one, please enter your name"
  - Error messages
- [ ] Mobile-first responsive design

### Phase 3: Loading Screen
- [ ] Create loading animation component
- [ ] Generate flattering loading messages (with translations):
  - "Compressing big amount of coolness"
  - "Getting things ready for such amazing person"
  - "Taking out the fancy cutlery"
  - "Polishing the red carpet"
  - "Alerting the paparazzi"
  - "Preparing confetti cannons"
- [ ] Ensure messages are culturally appropriate per language
- [ ] Add progress indicator or animated element
- [ ] Smooth transition to next screen

### Phase 4: Famous Namesakes Dialog
- [ ] Create dialog/modal component
- [ ] Implement AI-generated famous namesakes feature:
  - Use GitHub Actions with AI API to pre-generate list
  - Request AI to generate content in specified language
  - Store in generated JSON file
  - Display relevant famous people with same name
  - Fallback: "We are looking for [Username], is that you?"
- [ ] Add localized CTA button:
  - "No, I'm better than them" (English)
  - "No, soy mejor que ellos" (Spanish)
  - etc.
- [ ] Smooth background gradient transition (from data.md colors)

### Phase 5: Party Mode Activation
- [ ] Implement background gradient intensification (~10% shift)
- [ ] Create fireworks animation system:
  - Use Tabler Icons for cats/dogs based on `favoriteAnimal`
  - Particle system with icon-based sparks
  - Random burst patterns
  - Continuous animation
- [ ] Integrate audio playback:
  - YouTube embed API (hidden, audio-only) for national anthem
  - Fallback to generic celebration audio file
  - Auto-play with user gesture handling
- [ ] Cake animation:
  - SVG or CSS-based cake illustration
  - Slide up from bottom to center
  - 10-15 second animation duration

### Phase 6: Final Congratulations Screen
- [ ] Create birthday message layout:
  - Top: Localized "Happy Birthday" or "Happy [XX] Birthday"
    - "Happy Birthday" (en)
    - "Feliz Cumpleaños" (es)
    - "Joyeux Anniversaire" (fr)
    - "Alles Gute zum Geburtstag" (de)
    - "Feliz Aniversário" (pt)
    - "Buon Compleanno" (it)
    - "お誕生日おめでとう" (ja)
    - "生日快乐" (zh)
  - Center: Animated cake with custom message on base
  - Bottom: Localized "From [fromName]"
- [ ] Apply final background gradient from data.md
- [ ] Add subtle continuous animations (floating elements, sparkles)
- [ ] Ensure all animations are complete before showing

### Phase 7: GitHub Actions Automation
- [ ] Create workflow file (`.github/workflows/generate-site.yml`)
- [ ] Set up trigger on `data.md` changes
- [ ] Implement AI integration for:
  - Famous namesakes generation (in specified language)
  - Loading message variations (culturally appropriate)
  - Personalized content based on name/age/language
  - Respect language parameter for all AI-generated content
- [ ] Configure Astro build step
- [ ] Set up GitHub Pages deployment
- [ ] Add workflow status badge to README

### Phase 8: Documentation & Polish
- [ ] Write comprehensive README with:
  - Quick start guide emphasizing the **fork-per-friend workflow**:
    * "Fork this repo as `omg-hbd-john` for John (English)"
    * "Fork again as `omg-hbd-paco` for Paco (Spanish)"
    * Each fork = one person, one language
  - `data.md` field explanations (including language codes)
  - Supported languages list:
    * English (en), Spanish (es), French (fr)
    * German (de), Portuguese (pt), Italian (it)
    * Japanese (ja), Chinese (zh)
    * Add more as needed
  - Color palette suggestions by personality:
    * Energetic: Bright oranges, yellows (#FF6B35, #F7931E)
    * Calm: Blues, teals (#4ECDC4, #44A5C5)
    * Romantic: Pinks, purples (#FF6B9D, #C44569)
    * Professional: Navy, gold (#2C3E50, #F39C12)
    * Playful: Rainbow gradients
    * Elegant: Black, gold (#000000, #D4AF37)
  - Deployment instructions
  - Troubleshooting guide
- [ ] Add example `data.md` files for different languages
- [ ] Create demo GIF/video for README
- [ ] Add MIT license
- [ ] Test full workflow end-to-end with multiple language forks

### Phase 9: Optional Enhancements
- [ ] Add more animal options (birds, fish, etc.) with corresponding icons
- [ ] Implement confetti animation as alternative to fireworks
- [ ] Add photo upload feature for personalization
- [ ] Create multiple theme presets
- [ ] Add countdown timer feature
- [ ] Expand language support (Arabic RTL, Korean, Russian, etc.)
- [ ] Community translations contribution guide

## Technical Considerations

### Mobile-First Design
- All animations optimized for mobile performance
- Touch-friendly button sizes (min 44x44px)
- Reduced motion preferences respected
- Network-efficient assets

### Performance
- Lazy-load animations
- Preload critical assets
- Optimize SVG icons
- Minimize JavaScript bundle
- Use CSS animations over JavaScript where possible

### Accessibility
- Keyboard navigation support
- Screen reader friendly
- ARIA labels for interactive elements
- Color contrast compliance (WCAG AA)
- Respect `prefers-reduced-motion`
- HTML `lang` attribute set correctly based on selected language
- RTL support for languages like Arabic (future)

### Browser Compatibility
- Modern browsers (last 2 versions)
- Graceful degradation for older browsers
- Fallbacks for animation features

## File Structure
```
omg-hbd/
├── .github/
│   └── workflows/
│       └── generate-site.yml
├── src/
│   ├── components/
│   │   ├── NameEntry.astro
│   │   ├── LoadingScreen.astro
│   │   ├── FamousDialog.astro
│   │   ├── PartyMode.astro
│   │   ├── CongratulationsScreen.astro
│   │   └── Fireworks.astro
│   ├── layouts/
│   │   └── Layout.astro
│   ├── pages/
│   │   └── index.astro
│   ├── i18n/
│   │   ├── translations.js
│   │   ├── en.json
│   │   ├── es.json
│   │   ├── fr.json
│   │   ├── de.json
│   │   ├── pt.json
│   │   ├── it.json
│   │   ├── ja.json
│   │   └── zh.json
│   └── styles/
│       └── global.css
├── public/
│   ├── audio/
│   │   └── celebration.mp3
│   └── icons/
├── data.md
├── astro.config.mjs
├── package.json
├── README.md
└── .gitignore
```

## Success Criteria
- [ ] Complete site generation in under 2 minutes from `data.md` update
- [ ] Mobile-responsive on all screen sizes
- [ ] Smooth 60fps animations on modern devices
- [ ] Zero-configuration deployment to GitHub Pages
- [ ] Foolproof README that anyone can follow

## Notes & Concerns
- **Audio Autoplay**: Modern browsers restrict autoplay. May need user interaction first.
- **YouTube Embed**: Consider data usage for mobile users. Fallback is important.
- **AI API Costs**: GitHub Actions may need API key for AI features (OpenAI, Anthropic, etc.)
- **Performance**: Heavy animations may impact low-end devices. Add performance mode toggle?
- **Copyright**: Ensure all audio/music used is properly licensed or royalty-free.
- **Fork Strategy**: Each fork is a separate deployment for ONE person in ONE language. Simple and clean!

## Workflow Example
```bash
# For John (US, English)
git clone https://github.com/yourusername/omg-hbd.git omg-hbd-john
cd omg-hbd-john
# Edit data.md: name: "John", language: "en"
git push to new repo "omg-hbd-john"
# → Deploys to john.github.io/omg-hbd-john

# For Paco (Mexico, Spanish)  
git clone https://github.com/yourusername/omg-hbd.git omg-hbd-paco
cd omg-hbd-paco
# Edit data.md: name: "Paco", language: "es"
git push to new repo "omg-hbd-paco"
# → Deploys to paco.github.io/omg-hbd-paco

# For Kenji (Japan, Japanese)
git clone https://github.com/yourusername/omg-hbd.git omg-hbd-kenji
cd omg-hbd-kenji
# Edit data.md: name: "Kenji", language: "ja"
git push to new repo "omg-hbd-kenji"
# → Deploys to kenji.github.io/omg-hbd-kenji
```

## Next Steps
Once this plan is approved:
1. Initialize Astro project
2. Set up basic project structure
3. Create example `data.md`
4. Begin Phase 2 implementation
