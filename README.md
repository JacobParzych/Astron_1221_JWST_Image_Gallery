# JWST Image Gallery Organizer

**Astronomy 1221 - Project 2**  
**Authors:** Jacob Parzych & Niko Jamison

---

## 📖 Project Overview

This project creates a browsable catalog of James Webb Space Telescope (JWST) observations with comprehensive metadata organization and advanced image visualization. We extract metadata from astronomical FITS files, organize them into Pandas DataFrames for analysis, and create stunning false-color RGB composite images.

### Astronomy Context

The **James Webb Space Telescope (JWST)**, launched in 2021, is the most powerful space telescope ever built, observing in infrared wavelengths from 0.6 μm to 28 μm. This project works with FITS (Flexible Image Transport System) files - the standard astronomical image format containing both image data and extensive metadata in "headers." The `_i2d.fits` files are Level 3 calibrated, science-ready 2D images used in professional astronomy research.

---

## ✨ Key Features

### 1. **Automated Data Acquisition**
- Direct download from MAST Archive (Mikulski Archive for Space Telescopes)
- 16 JWST Early Release Observations across 4 iconic targets
- Complete NIRCam detector coverage (4 detectors per target)
- Progress bars and intelligent file existence checking

### 2. **Comprehensive Metadata Extraction**
- Extracts 25+ metadata fields from FITS headers
- Includes observation details: target, instrument, filter, exposure time
- Computes pixel statistics: min/max/mean/median/std/NaN counts
- WCS coordinates (RA/Dec) for astronomical positioning

### 3. **Pandas DataFrame Organization**
- Structured tabular data for easy manipulation
- Filtering and sorting capabilities
- Summary statistics grouped by target/detector
- Export-ready format (CSV/Excel compatible)

### 4. **Professional Astronomical Visualization**
- Proper ZScaleInterval + PowerStretch(a=2) image normalization
- Handles extreme dynamic range (>10,000:1)
- Individual image displays with detailed metadata
- Multi-panel comparison grids
- Complete 16-image detector mosaic gallery

### 5. **False-Color RGB Composites**
- Combines 3 infrared filters into viewable color images
- Automatic dimension matching with intelligent resampling
- Maps wavelengths to temperature/chemistry information
- F090W (0.9 μm) → Blue | F200W (2.0 μm) → Green | F444W (4.4 μm) → Red

---

## 🎯 Scientific Targets

### **NGC 3132 - Southern Ring Nebula**
- 4 NIRCam detectors (NRCB1-4)
- Planetary nebula with expanding gas shells
- Filter: F090W (0.9 μm infrared)

### **NGC 3324 - Carina Nebula (Cosmic Cliffs)**
- 4 NIRCam detectors
- Iconic star-forming region
- Filter: F090W

### **NGC 7320 - Stephan's Quintet**
- 4 NIRCam detectors
- Famous interacting galaxy group
- Filter: F090W

### **SMACS 0723 - Deep Field**
- 4 NIRCam detectors
- Thousands of distant galaxies through gravitational lensing
- Filter: F090W

### **M16 - Pillars of Creation (Eagle Nebula)**
- RGB composite target
- Filters: F090W, F200W, F444W
- Star-forming region with towering gas columns

---

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- Jupyter Notebook or JupyterLab
- ~2 GB free disk space for FITS files
- Stable internet connection for downloads

### Installation

1. **Clone the repository:**
```bash
git clone https://github.com/JacobParzych/Astron_1221_JWST_Image_Gallery.git
cd Astron_1221_JWST_Image_Gallery
```

2. **Install required packages:**
```bash
pip install -r requirements.txt
```

Or install directly in the notebook:
```python
%pip install astroquery astropy pandas matplotlib numpy tqdm scipy
```

3. **Launch Jupyter Notebook:**
```bash
jupyter notebook Project2_Parzych_Jamison.ipynb
```

---

## 📊 Project Workflow

### Phase 1: Data Acquisition (Cells 1-16)
- **Setup environment** and install packages
- **Download FITS files** from MAST Archive (16 observations, ~1.8 GB)
- **Verify file integrity** with size checks and inventory

### Phase 2: Metadata Extraction (Cells 17-24)
- **Parse FITS headers** with fallback strategies
- **Extract pixel statistics** from image data arrays
- **Create Pandas DataFrame** with 25 columns
- **Display complete catalog** with all metadata

### Phase 3: Analysis & Filtering (Cells 25-28)
- **Summary statistics** grouped by target/detector
- **Filter functions** for target-specific queries
- **Sort functions** by exposure time, brightness, contrast
- **Data quality assessment** with pixel statistics

### Phase 4: Visualization (Cells 29-34)
- **Individual image displays** with proper astronomical stretching
- **Multi-panel comparisons** (2×2 grid)
- **Complete gallery** (4×4 detector mosaic, 16 images)
- **Publication-quality outputs** saved as PNG files

### Phase 5: RGB Composites (Cells 35-38)
- **Manual download instructions** for multi-filter data
- **RGB composite creation** with automatic resampling
- **False-color interpretation** (blue=hot stars, red=cool dust)
- **4-panel visualization** (3 channels + composite)

---

## �� Usage Examples

### Running the Complete Pipeline

Execute cells sequentially from top to bottom:

```python
# 1. Install packages (Cell 4)
%pip install astroquery astropy pandas matplotlib numpy tqdm scipy

# 2. Import libraries (Cell 6)
import pandas as pd
import numpy as np
from astropy.io import fits
# ... (see notebook for complete imports)

# 3. Download data (Cells 8-13)
# Downloads 16 FITS files automatically

# 4. Extract metadata (Cell 20)
# Processes all files and creates DataFrame

# 5. Analyze and visualize (Cells 22-34)
# Generates plots and saves gallery images
```

### Filtering and Sorting

```python
# Filter by target
ngc3132 = filter_by_target(df, 'NGC 3132')

# Sort by exposure time
sorted_exp = sort_by_exposure(df, ascending=False)

# Sort by pixel brightness
sorted_brightness = sort_by_pixel_mean(df, ascending=False)
```

### Creating RGB Composites

1. Manually download F090W, F200W, F444W filters from [MAST Portal](https://mast.stsci.edu/portal/Mashup/Clients/Mast/Portal.html)
2. Place `_i2d.fits` files in `jwst_rgb_data/` directory
3. Run Cell 38 to create the composite

---

## 📁 Project Structure

```
Astron_1221_JWST_Image_Gallery/
├── Project2_Parzych_Jamison.ipynb    # Main analysis notebook
├── README.md                           # This file
├── requirements.txt                    # Python dependencies
├── jwst_data/                          # Downloaded FITS files (16 files)
│   ├── jw02731001001_02101_00001_nrcb1_i2d.fits
│   ├── jw02731001001_02101_00001_nrcb2_i2d.fits
│   └── ... (14 more files)
├── jwst_rgb_data/                      # RGB filter FITS files (manual download)
│   ├── pillars_of_creation_f090w.fits
│   ├── pillars_of_creation_f200w.fits
│   └── pillars_of_creation_f444w.fits
└── jwst_detector_mosaic_gallery.png    # Generated 16-image gallery
```

---

## 🛠️ Technical Details

### FITS File Structure

JWST `_i2d.fits` files are **Level 3 calibrated products**:
- **Extension 0 (Primary HDU):** Observation metadata
- **Extension 1 (SCI):** Calibrated 2D image data (typically 2048×2048 pixels)
- **Extensions 2+ (ERR/DQ):** Error maps and data quality flags

### Visualization Techniques

**Why not use matplotlib defaults?**  
JWST infrared images have extreme dynamic range (10,000:1+). Standard linear scaling shows only bright stars as white blobs and everything else as uniform gray.

**Our solution:**
- **ZScaleInterval:** IRAF/DS9 algorithm for intelligent min/max clipping
- **PowerStretch(a=2):** Quadratic transformation for contrast enhancement
- **AsinhStretch:** Inverse hyperbolic sine for RGB normalization
- **Origin='lower':** Astronomical convention (pixel [0,0] at bottom-left)

### RGB Composite Methodology

1. **Load 3 FITS files** (different wavelength filters)
2. **Check dimensions** - resample if mismatched using scipy.ndimage.zoom
3. **Normalize independently** - ZScale + Asinh for each channel
4. **Stack RGB cube** - np.dstack([red, green, blue])
5. **Interpret colors** - Red=cool dust, Green=warm gas, Blue=hot stars

---

## 📊 Dataset Statistics

- **Total observations:** 16 FITS files
- **Total data size:** ~1.8 GB (disk), ~0.26 GB (memory)
- **Targets:** 4 (NGC 3132, NGC 3324, NGC 7320, SMACS 0723)
- **Detectors:** 4 per target (NRCB1-4)
- **Filters:** F090W (0.9 μm) for base dataset
- **RGB filters:** F090W, F200W, F444W for M16
- **Pixels per image:** ~4 million (2048×2048)
- **Exposure times:** 236-837 seconds
- **NaN percentage:** ~1.5% (typical for NIRCam mosaics)

---

## 🔍 Key Functions

### `extract_fits_metadata(filepath)`
Extracts 25 metadata fields from FITS headers with intelligent fallback strategies.

### `create_rgb_composite(blue_file, green_file, red_file, title)`
Creates false-color RGB composites with automatic dimension matching.

### `display_fits_image(filepath, title, cmap)`
Displays FITS images with proper astronomical normalization.

### `filter_by_target(df, target_name)`
Filters DataFrame by target name (case-insensitive partial match).

### `sort_by_exposure(df, ascending)`
Sorts observations by integration time.

---

## 📚 Dependencies

- **astropy** (5.0+): FITS file I/O, WCS, visualization
- **pandas** (1.5+): DataFrame manipulation
- **numpy** (1.23+): Numerical computing
- **matplotlib** (3.6+): Plotting and visualization
- **scipy** (1.9+): Image resampling (ndimage.zoom)
- **astroquery** (0.4+): MAST Archive queries
- **tqdm** (4.64+): Progress bars

---

## 🎓 Educational Context

This project demonstrates professional astronomy workflows:

1. **Data discovery and retrieval** from astronomical archives
2. **FITS file handling** with Astropy
3. **Metadata organization** with Pandas
4. **Proper astronomical image display** (not "pretty pictures" but scientifically accurate visualizations)
5. **Multi-wavelength analysis** with RGB composites
6. **Reproducible research** with documented code

All data products are identical to those used in peer-reviewed publications. The JWST Early Release Observations featured in this project were released to the public in July 2022 and represent humanity's deepest infrared views of the universe.

---

## 🖼️ Sample Outputs

### Detector Mosaic Gallery
4×4 grid showing all 16 observations organized by target (rows) and detector (columns).  
**Output:** `jwst_detector_mosaic_gallery.png`

### RGB Composite
False-color image of Pillars of Creation combining F090W, F200W, and F444W filters.  
**Output:** `pillars_of_creation_rgb_composite.png`

---

## 🐛 Troubleshooting

### Downloads fail
- Check internet connection
- Verify MAST Archive is accessible: https://mast.stsci.edu
- Files may be temporarily unavailable during maintenance

### Memory errors
- Close other applications
- Process images one at a time
- Reduce image resolution if needed

### RGB dimension mismatch error
The notebook now automatically resamples images with mismatched dimensions using scipy. Ensure scipy is installed.

### Module not found
Run the installation cell (Cell 4) to install all required packages.

---

## 📖 Additional Resources

- **JWST Documentation:** https://jwst-docs.stsci.edu/
- **MAST Archive:** https://mast.stsci.edu/
- **Astropy Documentation:** https://docs.astropy.org/
- **FITS Standard:** https://fits.gsfc.nasa.gov/

---

## 📄 License

This project is for educational purposes as part of Astronomy 1221. JWST data is public domain (NASA).

---

## �� Authors

- **Jacob Parzych**
- **Niko Jamison**

---

*"The James Webb Space Telescope is revealing the universe as never seen before." - NASA*

