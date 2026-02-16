# OMG Happy Birthday 🎉

A static website generator to create emergency celebration messages. Surprises when you totally forgot it, in a matter of few minutes you will have a nice page. The system automates the creation of an interactive, personalized page that can be quickly deployed to GitHub Pages.

## Quick Start

### The Fork-per-Friend Workflow
1. **Fork** this repo as `omg-hbd-john` for John (English).
2. **Clone** it: `git clone ...`
3. **Copy and edit**: `cp data.example.md data.md`
4. **Edit** `data.md` with John's details.
5. **Process it with Copilot** `copilot` then `follow plan.md steps to create a congratulations website`
6. **Confirm and Wait** Check Copilot suggestions and changes to build your landing page
7. **Push** changes. The site will automatically be visible on to GitHub Pages!

### Configuration (`data.md`)

Edit `data.md` in the root directory to personalize the experience.

```yaml
language: "en" # ui options: en, es, fr, de, etc.
name: "Bryan" # The name of your special one
favorites: "dogs,videogames" # options: cat, dog, soccer, swimming or custom
favoriteColor: "blue" # options: #hexvalue or name
bgColor: "#D6EADF" # options: #hexvalue or name
fromName: "Your Friend Steve" # who is sending this
celebrationTitle: "Happy 40th Anniversary!" # Main greeting
customMessage: "My best wishes..." # A custom message
youtubeSongUrl: "https://www.youtube.com/watch?v=dQw4w9WgXcQ" # Background Music
```

### Supported Languages
Ensure `messages.md` content matches your chosen language. By default, English (en) is provided.
- English (en)
- Spanish (es) - *Update messages.md manually*
- French (fr) - *Update messages.md manually*

### Color Palette Suggestions
* **Energetic**: Bright oranges, yellows (`#FF6B35`, `#F7931E`)
* **Calm**: Blues, teals (`#4ECDC4`, `#44A5C5`)
* **Romantic**: Pinks, purples (`#FF6B9D`, `#C44569`)
* **Professional**: Navy, gold (`#2C3E50`, `#F39C12`)
* **Elegant**: Black, gold (`#000000`, `#D4AF37`)

## Deployment

This project build the static site into `docs` folder, so a public webpage will be available once you push it.

## Local Development

1. Navigate to the app directory:
   ```bash
   cd omg-hbd-app
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Run the development server:
   ```bash
   npm run dev
   ```
4. Open [http://localhost:3000](http://localhost:3000).

## License
MIT
