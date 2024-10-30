# Domain-driven-module-generator

This project provides a command-line tool to automatically generate module structures for a TypeScript-based project. The structure of each module is defined in a JSON file, making it flexible and easy to update.

## Features

- Dynamically generates a module structure based on a JSON configuration file.
- Supports nested directory creation and dynamic file naming.
- Easily extendable and maintainable with a single JSON structure definition.

## Prerequisites

- **Node.js** (v14 or higher)
- **TypeScript** (v4 or higher)

## Setup

### 1. Clone the Repository

```bash
git clone https://github.com/TusharSync/domain-driven-module-generator.git
cd domain-driven-module-generator
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure TypeScript

Ensure you have a `tsconfig.json` file with the following key options:

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "resolveJsonModule": true,
    "esModuleInterop": true,
    "outDir": "./dist"
  }
}
```

## Directory Structure

```
src/
├── application/
│   └── <moduleName>/
│       ├── tests/
│       │   └── index.ts
│       ├── interface.d.ts
│       ├── index.ts
│       └── <moduleName>.services.ts
├── interface/
│   └── <moduleName>/
│       ├── tests/
│       │   └── index.ts
│       ├── <moduleName>.controller.ts
│       ├── <moduleName>.router.ts
│       ├── index.ts
│       ├── response.messages.ts
│       └── schema.ts
└── domain/
    └── <moduleName>/
        ├── tests/
        │   └── index.ts
        ├── index.ts
        ├── <moduleName>.repository.ts
        └── types.d.ts
```

## Usage

### 1. Define Your Module Structure

Modify the `module-structure.json` file if needed:

```json
{
  "application": {
    "tests": {
      "files": ["index.ts"]
    },
    "files": ["interface.d.ts", "index.ts", "<moduleName>.services.ts"]
  },
  "interface": {
    "tests": {
      "files": ["index.ts"]
    },
    "files": ["<moduleName>.controller.ts", "<moduleName>.router.ts", "index.ts", "response.messages.ts", "schema.ts"]
  },
  "domain": {
    "tests": {
      "files": ["index.ts"]
    },
    "files": ["index.ts", "<moduleName>.repository.ts", "types.d.ts"]
  }
}
```

### 2. Run the Generator

To generate a module, use the following command:

```bash
npm run generate <module-name>
```

For example, to generate a module named `user`:

```bash
npm run generate user
```

### 3. Check the Output

The script will automatically generate the directory and file structure based on the JSON configuration.

## Customization

- **JSON Structure**: You can easily extend or modify the structure in the `module-structure.json` file. Add new directories, files, or even dynamic placeholders like `<moduleName>`.
- **File Templates**: The script creates empty files, but you can update the `createFile` function to add boilerplate content to specific files based on your needs.

## Project Structure

```
src/
├── scripts/
│   ├── generate-module.ts       # Main script to generate the module structure
│   └── module-structure.json    # JSON file defining the module structure
```

## Contributing

If you would like to contribute to this project, feel free to open a pull request or an issue.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.
