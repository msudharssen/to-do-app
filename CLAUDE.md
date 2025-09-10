# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a .NET 9.0 Blazor Server application implementing a simple To-Do list. The application uses interactive server components with real-time updates.

## Common Commands

### Development
```bash
dotnet restore          # Restore NuGet packages
dotnet run             # Run the application (accessible at https://localhost:5001)
dotnet build           # Build the project
dotnet clean           # Clean build artifacts
```

### Testing
```bash
dotnet test            # Run tests (if test projects exist)
```

## Architecture & Structure

### Core Components
- **Program.cs**: Application entry point, configures services and middleware
- **TodoItem.cs**: Simple data model with Title and IsCompleted properties
- **Components/**: Contains all Blazor components organized by purpose
  - **Pages/**: Routable page components (`@page` directive)
    - **Todo.razor**: Main todo functionality at `/todo` route with InteractiveServer render mode
  - **Layout/**: Layout components (MainLayout, NavMenu)
  - **App.razor**: Root application component with HTML document structure
  - **Routes.razor**: Router configuration
  - **_Imports.razor**: Global using statements for all components

### Key Architectural Patterns
- **Blazor Server with Interactive Components**: Uses `@rendermode InteractiveServer` for real-time UI updates
- **Component-based Architecture**: Separates concerns between layout, pages, and reusable components
- **In-memory State Management**: Todo items stored in component state (not persisted)

### Todo Component Structure
The main Todo page (`Components/Pages/Todo.razor`) demonstrates:
- Two-way data binding with `@bind`
- Event handling with `@onclick`
- Component state management with private fields
- Inline C# code in `@code` blocks

### Styling & Assets
- Uses Bootstrap 5 for styling
- Static assets in `wwwroot/` directory
- Component-specific styles via `BlazorApp1.styles.css`

## Development Notes

- Target framework: .NET 9.0
- Nullable reference types enabled
- Implicit usings enabled
- No external data persistence (todos are lost on app restart)
- Uses Blazor's new static asset system (`@Assets[]`)