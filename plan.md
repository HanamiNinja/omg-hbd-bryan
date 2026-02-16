# OMG Happy Birthday - Implementation Plan

## Project Overview
A static website generator for emergency birthday or small celebration. Surprises when you totally forgot it in a matter of few minutes. The system automates the creation of an interactive, personalized page that can be quickly deployed to GitHub Pages.

## Technology Stack
User selectable via `config.md`, recomended by default.

## Data Structure

User customizable via `data.md`, please take some minutes to be as especific as you want.

## Implementation Workplan

### Phase 1: Planning
- [ ] Read `data.md` to understand celebration context and the tastes of the person being celebrated.
- [ ] The following steps should be interpreted every time based on the properties of `data.md`, props are represented as `propName` Ask for user confirmation before proceeding the next phase. 
- [ ] All dialog options or message suggestions should be in the `language` the user specified.
- [ ] Workflow screens:
  - [ ] "Welcome form", this is a dialog that asks for the name with a caption "The most important/cool/great person that loves `favorites`, we have an important message for he-she", then an iput area that splits every char of the `name` appears, for example for "Pancho" should be "P _ _ _ _ O", for Ale85 "A _ _ _ 5" and so on. So suggest the message and confirm the name we are going to use. If the name matches, go to the next screen, if not just buzz the dialog
  - [ ] "Loading Screen", will show a fake loading, about 8-10 seconds and shows random messages
  - [ ] "Cake Appearing", Copilot will geneare a cake based on the user's `favorites` and `favoriteColor`, this image will fade in in from the very botttom to the middle, the opacity and possition will take 3 seconds to be in place with a bounce-out animation.
  - [ ] "Party Mode", On the background `youtubeSongUrl` start playing as background music with the simpliest volume controls (play, stop), in the meantime `celebrationTitle` will appear on the top of the cake, big size and bouncing, and finally `customMessage` will appear on the bottom of the cake, multiline if it's needed
- [ ] Once every step is confirmed, generate a `messages.md` generate an option of all messages and ask for approval from user, take in cosideration all the messages needed in all phases described in this document ("Welcome Form", "Loading Screen" and "Final Congratulations Screen")
- [ ] Ensure all messages are culturally appropriate for the celebrated language
- [ ] Then look if you have skills to generate the cake image (DALL-E 3, Nanobanana or another skill), if not, ask to the user to set an option for the cake image.

### Phase 2: Project Setup & Scaffolding
- [ ] Read `config.md` to define technology stack
- [ ] Create scaffolding script/workflow that based on `config.md` specs, THE SOURCE CODE of the page should be under the `omg-hbd-app` folder to avoid pushing it to github by default, only the build is needed for deployment into the page.
- [ ] Before start ensure it's simple o deploy a project with the selected stack and autoverify if we have everithing that it's needed to deploy the build at the end:
  - If `nextjs`: Initialize Next.js project
  - If `astro`: Initialize Astro project
  - If `html`: Setup basic HTML/CSS/JS structure
- [ ] Configure GitHub Pages deployment based on selected stack
- [ ] Create basic project structure (components, layouts, pages) adapted to chosen stack
- [ ] Configure all other integrations for styling like: Components, icons, images and everything that will be needed
- [ ] Create configuration files like `.gitignore`, Github Actions for deployment, if you need to customize actions on `package.json` in case it's needed
- [ ] Projec build should place all files on `/docs` of this folder to generate the corresponding github page, please change the configuration of `npm run build` o equivalent

### Phase 3: Welcome Form
- [ ] Read `data.md` and `messages.md` to get context and the required messages
- [ ] General Layout and styling definition
  - [ ] Based on the `bgColor` prop, decide whether the theme will be dark or ligth
  - [ ] Set a main a diagonal gradient with a 5%-10% variation based on the `bgColor`
- [ ] The initial from it's a Dialog with etter hint input fields (e.g., "B _ _ _ _ N")
  - Individual input boxes for each letter
  - Show first and last letter as hints
  - Auto-focus on first empty field
  - Auto-advance to next field on input
- [ ] Add name validation logic
  - Compare entered name with `data.md` configuration
  - Show localized "Not cool enough" alert on mismatch
  - Trigger loading screen on correct name
- [ ] Add localized text based on the `messages.md` for the intro:
  - "We are looking for a super special one, please enter your name"
  - Error messages
- [ ] Mobile-first responsive design

### Phase 4: Loading Screen
- [ ] Read `data.md` and `messages.md` to get context and the required messages
- [ ] Create loading animation component, will last for 8-10 seconds
- [ ] Randomly rotates loading messages (with translations):
  - "Compressing big amount of coolness"
  - "Getting things ready for such amazing person"
  - ...
- [ ] Add progress indicator or animated element
- [ ] Smooth transition to next screen

### Phase 5: Cake Appearing
- Place the cake on the bottom totally transparent
- The animation to the middle will last 3-5 seconds with a small bounce at the end
- The same for the opacity to 100%
- [ ] Integrate audio playback:
  - YouTube embed API (hidden, audio-only) for `youtubeSongUrl`
  - Auto-play with user gesture handling


### Phase 6: Party Mode Activation
- [ ] Create fireworks animation system:
  - Use Tabler Icons for cats/dogs based on `favoriteAnimal`
  - Particle system with icon-based sparks
  - Random burst patterns
  - Continuous animation
- [ ] The messages appear in the following layout:
  - Top: Localized `celebrationTitle`
  - Bottom: `customMessage`
  - Bottom: `fromName`
- [ ] Add subtle continuous animations (floating elements, sparkles)
- [ ] Ensure all animations are complete before showing

## GitHub Actions Automation
- [ ] Create workflow file (`.github/workflows/generate-site.yml`)
- [ ] Set up trigger on `data.md` changes
- [ ] Implement AI integration for:
  - Loading message variations (culturally appropriate)
  - Personalized content based on name/age/language
  - Respect language parameter for all AI-generated content
- [ ] Configure Framework build step
- [ ] Set up GitHub Pages deployment
- [ ] Add workflow status badge to README

## Technical Considerations

### Mobile-First Design
- All animations optimized for mobile performance
- Touch-friendly button sizes (min 44x44px)
- Reduced motion preferences respected
- Network-efficient assets

### Performance
- Lazy-load animations
- Preload critical assets
- Optimize SVG icons if needed
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

## Success Criteria
- [ ] Complete site generation in under 5 minutes from `data.md` update
- [ ] Mobile-responsive on all screen sizes
- [ ] Smooth 60fps animations on modern devices
- [ ] Zero-configuration deployment to GitHub Pages
