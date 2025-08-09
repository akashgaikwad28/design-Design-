# Document Editor System

A modular document editor system demonstrating system design principles with clean architecture and separation of concerns.

## Architecture Overview

This system follows a modular architecture with clear separation between:

- **Interfaces**: Define contracts for system components
- **Elements**: Concrete implementations of document elements
- **Models**: Core business logic and data structures
- **Storage**: Different persistence mechanisms
- **Controllers**: Application logic and user interactions
- **Client**: Entry point and demonstration

## Project Structure

```
document_Editor/
├── interfaces/
│   ├── DocumentElement.java    // Interface for document elements
│   └── Persistence.java        // Interface for storage mechanisms
├── elements/
│   ├── TextElement.java        // Text content element
│   ├── ImageElement.java       // Image content element
│   ├── NewLineElement.java     //  Line break element
│   └── TabSpaceElement.java    //  Tab space element
├── models/
│   └── Document.java           // Document model class
├── storage/
│   ├── FileStorage.java        // File-based persistence
│   └── DBStorage.java          // Database persistence (placeholder)
├── controllers/
│   └── DocumentEditor.java     // Main controller class
├── client/
│   └── DocumentEditorClient.java // Demo application
└── README.md                   // This file
```

## Design Patterns Used

1. **Strategy Pattern**: Different storage mechanisms (FileStorage, DBStorage)
2. **Composite Pattern**: Document composed of multiple elements
3. **Factory Pattern**: Element creation through constructors
4. **Dependency Injection**: Storage mechanism injected into DocumentEditor
5. **Interface Segregation**: Clean interfaces for extensibility

## Usage

### Basic Usage

```java
// Create components
Document document = new Document();
FileStorage storage = new FileStorage("output.txt");
DocumentEditor editor = new DocumentEditor(document, storage);

// Add content
editor.addText("Hello World");
editor.addImage("picture.jpg");
editor.addNewLine();

// Render and save
System.out.println(editor.renderDocument());
editor.saveDocument();
```

### Advanced Usage

```java
// Use different storage
DBStorage dbStorage = new DBStorage();
DocumentEditor dbEditor = new DocumentEditor(document, dbStorage);

// Custom file name
FileStorage customStorage = new FileStorage("mydocument.txt");
```

## Extending the System

### Adding New Element Types

1. Create new class in `elements/` package
2. Implement `DocumentElement` interface
3. Add rendering logic in `render()` method

### Adding New Storage Types

1. Create new class in `storage/` package
2. Implement `Persistence` interface
3. Implement `save()` method with your storage logic

### Adding New Features

1. Extend `Document` class in `models/`
2. Add methods to `DocumentEditor` in `controllers/`
3. Update client code in `client/`

## System Design Principles Applied

- **Single Responsibility Principle**: Each class has one clear purpose
- **Open/Closed Principle**: Open for extension, closed for modification
- **Liskov Substitution Principle**: Storage implementations are interchangeable
- **Interface Segregation Principle**: Focused interfaces
- **Dependency Inversion Principle**: High-level modules don't depend on low-level modules

## Running the System

Compile and run the client:

```bash
javac client/DocumentEditorClient.java
java client.DocumentEditorClient
```

## Future Enhancements

- Add loading functionality
- Implement actual database storage
- Add formatting options (bold, italic, etc.)
- Add undo/redo functionality
- Add document validation
- Add configuration management
- Add logging system
- Add unit tests
