# 🌱Mod Manager Requirements for PVZ-RH Mods

To ensure your mod is correctly indexed and displayed in the automated PVZ:RH Mod Indexer, your repository must follow the structure and rules below.

If any required file or field is missing, your mod will be added to skip-report.json with the reason.

---

## 📁 Required Files in Repository Root

Your repository must contain the following files in the root directory:
```
/
├── mod.json          # Required
├── icon.png          # Optional (recommended)
└── Description.md    # Optional
```
## ✔ mod.json (required)

Defines your mod’s metadata. Must be valid JSON and include all required fields.

A template is provided below.

## ✔ GitHub Release (required)

Your repository must have at least one GitHub Release with one asset.

The indexer uses:

The latest release

The first asset in that release

The asset name to determine loader type (if ambiguous)

## ✔ icon.png (optional but recommended)

Used as the mod’s thumbnail in the game

Recommend size is 256x256

## ✔ Description.md (optional)

Markdown description of your mod.If missing → description: null.

## 🧩 Required Fields in mod.json
 Your mod.json must include the following fields:

| Field         | Type     | Description                                      |
|---------------|----------|--------------------------------------------------|
| `Id`          | string   | Unique internal mod ID                           |
| `name`        | string   | Display name of the mod                          |
| `creator`     | string   | Name of the mod author or team                   |
| `version`     | string   | Mod version (e.g., `"1.0.0"`)                    |
| `teaser`      | string   | Short description shown in mod listings          |
| `loader`      | string   | `"melon"`, `"bepinex"`, or `"melon/bepinex"`     |
| `gameVersion` | string   | Comma-separated list of supported game versions  |

---

## 🎯 Loader Rules

Valid loader values:

"melon"
"bepinex"
"melon/bepinex"

If you use "melon/bepinex", the indexer will determine the final loader based on your release asset name:

Contains bepinex_ → BepInEx

Contains melonloader_ → MelonLoader

Contains both or neither → included in both lists

## 🧪 Game Version Format

gameVersion must be a string, not an array.

Example:
"3.2.1"

Treated as minimum game version if one
Treated as range if two
Treated as specific if three +

Advanced Example:
"3.1.1" will work on 3.2.1 
"3.0.1, 3.2.1" will work in this range
"3.0.1, 3.1.1, 3.2.1" will work for these three specific
"3.0.1, 0, 0" only works for 3.0.1

## 📄 Template mod.json

Use this as a starting point:
```
{
  "Id": "your.unique.mod.id",
  "name": "Your Mod Name",
  "creator": "Your Name",
  "version": "1.0.0",
  "teaser": "A short description of your mod.",
  "loader": "melon",
  "gameVersion": "3.1.1, 3.0.1",
  "tags": ["fun", "content"]
}
```
## 📁 Expected Files In Release

Your release must contain the following files in the root directory:
```
/
├── mod.json          # Optional (recommended)
├── icon.png          # Optional (recommended)
├── Description.md    # Optional
├── /Mods             # If MelonMod or Both
└── /BepInEx          # If BepInExMod or Both
    └── /plugins

```

## 🚀 Publishing Your Mod

 -  Push your repository to GitHub

 - Create a Release

 - Upload your mod file as a release asset

 - The indexer will automatically detect your mod within 5 hours

 #### If something is wrong, check skip-report.json in the index repo

## 🛠 Troubleshooting

If your mod does not appear in the index:

 - Check skip-report.json for the reason

 - Ensure mod.json is valid JSON

 - Ensure all required fields are present

 - Ensure you have a GitHub Release with at least one asset

 - Ensure gameVersion is a string, not an array

 - Ensure loader is one of the valid values
