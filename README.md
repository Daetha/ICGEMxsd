# 🌍 ICGEM XML Schema Documentation

Welcome to the **International Centre for Global Earth Models (ICGEM)** XML Schema repository! This schema defines the structure for global gravity field models and their metadata.

---

## 📖 Quick Links

| Resource | Purpose |
|----------|---------|
| [ICGEM Website](https://icgem.gfz.de/home) | Browse & access global gravity field models |
| [ELMO Editor](https://env.rz-vm182.gfz.de/elmo-gem) | Create & edit model metadata using the interactive editor |
| [Schema Structure](https://docs.google.com/spreadsheets/d/18Akf4Xj_rXxgsQfJNDHXsn8dxHTEYMZT2jzb5ZxpP0A/edit?gid=1997633139#gid=1997633139) | View complete schema in tabular format |

---

## 🏗️ Schema Structure

### Conceptual diagram
![ICGEM Schema Architecture](img/conceptual diagram.png)

### Root Element: `globalGravityProduct`

This is the main container for all gravity field models. It can contain one of three model types:

#### 1. **Spherical Harmonic Models** (GGM)
Mathematical representations of the geopotential using spherical harmonics.

**Key Properties:**
- `modelName` - Name of the gravity model
- `publicationYear` - Year of publication (YYYY format)
- `modelType` - Type of model (static, temporal, topographic, etc.)
- `mathematicalRepresentation` - Details about the harmonic representation
- `degreeOrderMax` - Maximum degree and order of harmonics
- `earthGravityConstant` - GM value in m³/s²
- `radius` - Reference radius in meters
- `tideSystem` - Tide system used (e.g., tide-free, mean-tide)
- `errors` - Uncertainty information
- `fileFormat` - Format of the model file

#### 2. **MASCON Models** (Mass Concentration)
Grid-based mass anomaly representations.

**Key Properties:**
- `longitude`, `latitude` - 
- `dataEWH` - Equivalent Water Height
- `uncertainty` - 
- `masconID` - 

#### 3. **Altimetry Models**
Satellite altimetry-derived gravity models.

**Key Properties:**
- `longitude`, `latitude`, `time` - 
- `uncertainty` -
- `landMask` - 

---

## ㍽ Naming convention

To ensure consistency across the registry and compatibility with our database exports, all XSD files must adhere to the following naming standards:

| Type of Component | Style | Example |
| :--- | :--- | :--- |
| **Elements** | `camelCase` | `<xs:element name="modelName" ... />` |
| **Complex/Simple Types** | `camelCase` | `<xs:complexType name="temporalModelsProperties" />` |
| **Enumeration Values** | `Sentence case` | `<xs:enumeration value="Satellite altimetry" />` |
| **Attributes** | `lowercase` | `<xs:attribute name="type" ... />` |

- Sentence case means the following: "First letter in senntence is capital other words are separated with spaces"
- If possible, the name of the element and the type of the element are the same. The definitions of type do not receive a type suffix. 

#### Example: 
`<xs:element name="ellipsoidalParameters" type="ellipsoidalParameters" minOccurs="0"/>`
Easy and simple!

---

## 📊 Model Types

Each model can be one of the following types:

- **Static Models** - Mean models with a referece to a certain time point
- **Temporal Models** - Time-specific gravity field representations (recreated each release)
- **Topographic Models** - Gravity models derived from indirect gravity measurements

---

## 🔗 Input Data Sources

Models can reference multiple input data sources with specific details:

| Source Type | Details |
|------------|---------|
| **Satellite** | Satellite mission data (e.g., GRACE, GOCE, SLR) |
| **Ground** | Ground-based gravity measurements |
| **Altimetry** | Satellite altimetry data |
| **Elevation/Terrain** | Topographic and terrain models (with optional isostasy compensation) |
| **Model** | Data from other gravity models |

---

## 🛠️ Using the Schema

### With ELMO Editor
The **ELMO (GFZ Data Services' Metadata Editor)** provides a user-friendly interface to:
- ✅ Create new model metadata
- ✅ Generate XML that conforms to this schema

**Access:** [ELMO for ICGEM](https://env.rz-vm182.gfz.de/elmo-gem)

### Direct XML Usage
Use the schema files to validate your XML documents:
- Main schema: `globalGravityProduct.xsd`
- Include schemas in `include/` folder for modular validation

---

## 📁 File Organization

```
icgem-xml-schema/
├── globalGravityProduct.xsd          # Main schema definition
├── include/
│   ├── description.xsd
│   ├── ellipsoidalParameters.xsd
│   ├── errors.xsd
│   ├── fileFormat.xsd
│   ├── inputDataSource.xsd
│   ├── mathematicalRepresentation.xsd
│   ├── modelType.xsd
│   ├── staticModelProperties.xsd
│   ├── temporalModelProperties.xsd
│   ├── tideSystem.xsd
│   ├── topographicModelProperties.xsd
│   └── include4datasources/          # Data source definitions
│       ├── altimetryDetails.xsd
│       ├── elevationTerrainDetails.xsd
│       ├── groundDetails.xsd
│       ├── inputDataSourceType.xsd
│       └── modelDetails.xsd
└── README.md                          # This file
```

---

## 🌐 About ICGEM

The **International Centre for Global Earth Models** is part of the **International Gravity Field Service (IGFS)** under the **International Association of Geodesy (IAG)**.

ICGEM provides:
- 📦 Archive of all existing global gravity field models
- 🎨 Web-based visualization tools
- 🧮 Calculation services for gravity field functionals
- 📚 Tutorials and documentation
- 🆔 Digital Object Identifiers (DOI) for gravity products

**Learn more:** [icgem.gfz.de](https://icgem.gfz.de/home)

---

## 📞 Support & Contact

- **Email:** icgem@gfz.de
- **Mailing List:** [Subscribe to ICGEM-users](https://www.listserv.dfn.de/sympa/subscribe/icgemusers)
- **Questions?** Visit the [FAQ](https://icgem.gfz.de/faq) or [contact ICGEM](https://icgem.gfz.de/contact)

---

*Last updated: January 2026*  
*For the latest schema details, consult the [schema structure spreadsheet](https://docs.google.com/spreadsheets/d/18Akf4Xj_rXxgsQfJNDHXsn8dxHTEYMZT2jzb5ZxpP0A/edit?gid=1997633139#gid=1997633139).*
