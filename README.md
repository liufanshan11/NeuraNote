# NeuraNote - Modern Note Taking App

A modern, intuitive note-taking web application built with Vue 3, TypeScript, and Tailwind CSS. Features real-time markdown editing, bidirectional linking, graph visualization, and persistent local storage.

## ✨ Features

### Core Functionality
- 📝 **Real-time Markdown Editing** - Live editing with split-view, editor-only, and preview-only modes
- 🔗 **Bidirectional Linking** - Create connections between notes using `[[note-name]]` syntax
- 🎯 **Smart Organization** - Tag-based categorization and advanced filtering
- 🔍 **Full-text Search** - Fast search across all notes and content
- 💾 **Local Storage** - Persistent client-side storage using IndexedDB
- 🎨 **Theme Support** - Light/dark mode with user preferences

### Advanced Features
- 📊 **Graph Visualization** - Interactive force-directed graph showing note relationships
- 🔄 **Backlink Tracking** - Automatic detection and display of incoming links
- 🏷️ **Tag Management** - Create, edit, and filter notes by tags with automatic counting
- 📱 **Responsive Design** - Works seamlessly on desktop, tablet, and mobile devices
- ⚡ **Performance Optimized** - Debounced updates and efficient data processing

## 🛠️ Tech Stack

- **Frontend Framework**: Vue 3 with Composition API
- **Language**: TypeScript for type safety
- **Build Tool**: Vite for fast development and building
- **Styling**: Tailwind CSS for utility-first styling
- **State Management**: Pinia (Vuex alternative)
- **Storage**: Dexie.js for IndexedDB client-side storage
- **Markdown Processing**: marked.js for real-time parsing
- **Graph Visualization**: D3.js for interactive force-directed graphs
- **Package Manager**: npm

## 📁 Project Structure

```
neuranote/
├── src/              # Source code
│   ├── components/   # Vue components
│   │   ├── NoteEditor.vue      # Markdown editor with real-time preview
│   │   ├── Sidebar.vue         # Note navigation and filtering
│   │   ├── BacklinksPanel.vue  # Backlinks display and navigation
│   │   ├── GraphView.vue       # D3.js graph visualization
│   │   └── NotePropertiesModal.vue # Note metadata editing
│   ├── stores/       # Pinia state management
│   │   ├── note.ts   # Note state and operations
│   │   ├── ui.ts     # UI state and preferences
│   │   └── graph.ts  # Graph data and visualization state
│   ├── storage/      # Data persistence layer
│   │   └── database.ts # IndexedDB database operations
│   ├── utils/        # Utility functions
│   │   └── linkManager.ts # Bidirectional link management
│   ├── App.vue       # Main application component
│   ├── main.ts       # Application entry point
│   └── style.css     # Global styles
├── document/         # Project documentation
├── public/           # Static assets
├── package.json      # Dependencies and scripts
├── vite.config.ts    # Vite configuration
├── tsconfig.json     # TypeScript configuration
├── tailwind.config.js # Tailwind CSS configuration
└── postcss.config.js # PostCSS configuration
```

## 🚀 Getting Started

### Prerequisites
- Node.js 16.0 or higher
- npm or yarn package manager

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd neuranote
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start development server**
   ```bash
   npm run dev
   ```
   The application will be available at `http://localhost:5173`

### Building for Production

1. **Build the application**
   ```bash
   npm run build
   ```
   This creates a `dist/` folder with optimized production files.

2. **Preview production build**
   ```bash
   npm run preview
   ```
   Preview the production build locally before deployment.

### Deployment

#### Option 1: Static Hosting (Recommended)
NeuraNote is a static web application that can be deployed to any static hosting service:

**Netlify**
1. Connect your repository to Netlify
2. Set build command: `npm run build`
3. Set publish directory: `dist`
4. Deploy automatically on git push

**Vercel**
1. Import your repository to Vercel
2. Vercel will automatically detect Vite configuration
3. Deploy with zero configuration

**GitHub Pages**
1. Build the project: `npm run build`
2. Deploy the `dist` folder to GitHub Pages
3. Configure proper base path in `vite.config.ts`

#### Option 2: Traditional Web Server
1. Build the project: `npm run build`
2. Upload the contents of the `dist` folder to your web server
3. Configure your server to serve `index.html` for all routes (SPA routing)

### Environment Configuration

For production deployment, you may want to configure:

```javascript
// vite.config.ts
export default defineConfig({
  base: process.env.NODE_ENV === 'production' ? '/your-repo-name/' : '/',
  // ... other config
})
```

## 📚 Usage Guide

### Creating Notes
1. Click the "+" button in the sidebar to create a new note
2. Start typing your content using Markdown syntax
3. Use the view mode buttons to switch between editor, preview, or split view

### Bidirectional Linking
- Use `[[note-name]]` syntax to create links to other notes
- Links appear with green background and double brackets for visual distinction
- Click any link to navigate to the referenced note
- View backlinks in the Backlinks panel to see which notes link to the current note

### Tagging Notes
1. Click the edit button (pencil icon) on any note in the sidebar
2. Add tags in the properties modal
3. Use the tag filter in the sidebar to view notes by tag

### Graph Visualization
1. Click the graph view button (🔄) in the header
2. Explore your note relationships in the interactive graph
3. Click nodes to navigate to notes
4. Use mouse wheel to zoom and drag to pan

### Keyboard Shortcuts
- `Ctrl/Cmd + N` - Create new note
- `Ctrl/Cmd + F` - Focus search
- `Ctrl/Cmd + S` - Save current note
- `Ctrl/Cmd + /` - Toggle theme

## 🐛 Troubleshooting

### Common Issues

**Build fails with TypeScript errors**
```bash
npm run build -- --force
```

**Development server not starting**
```bash
rm -rf node_modules package-lock.json
npm install
```

**IndexedDB data issues**
Clear browser storage for the application domain to reset the database.

## 📖 Documentation

Complete project documentation is available in the [`document/`](document/) folder:

- [`project-overview.md`](document/project-overview.md) - Project vision and core concepts
- [`architecture-design.md`](document/architecture-design.md) - Technical architecture and design decisions
- [`markdown-editor-implementation.md`](document/markdown-editor-implementation.md) - Markdown editor implementation details
- [`bidirectional-linking-implementation.md`](document/bidirectional-linking-implementation.md) - Bidirectional linking system
- [`graph-visualization-implementation.md`](document/graph-visualization-implementation.md) - Graph visualization implementation
- [`ui-ux-enhancements.md`](document/ui-ux-enhancements.md) - UI/UX improvements and fixes
- [`project-development-report.md`](document/project-development-report.md) - Comprehensive development report (Chinese)

## 🤝 Development

### Contributing
1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'Add amazing feature'`
4. Push to the branch: `git push origin feature/amazing-feature`
5. Open a pull request

### Development Scripts
```bash
npm run dev          # Start development server
npm run build        # Build for production
npm run preview      # Preview production build
npm run lint         # Run ESLint
npm run type-check   # Run TypeScript type checking
```

### Code Standards
- Follow Vue 3 Composition API best practices
- Use TypeScript for type safety
- Write comprehensive unit tests
- Ensure responsive design across devices
- Follow accessibility guidelines (WCAG)

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- Vue.js team for the excellent framework
- Tailwind CSS for the utility-first CSS framework
- D3.js for powerful data visualization capabilities
- Dexie.js for robust IndexedDB integration

---

**NeuraNote** - Organize your thoughts, connect your ideas. 🧠✨