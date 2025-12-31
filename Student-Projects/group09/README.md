# 🎯 Object Detection with YOLOv8 - Complete Project

<div align="center">

## GROUP 9 
1. Hanie Asali (Team Leader)
2. Hanie Lari
3. Reihane Partovi
4. Sara Eghdami
5. Mahsa mehabadi

## 🚀 Object Detection Web Application

<video width="800" controls loop muted playsinline style="border-radius: 8px;">
  <source src="assets/demo.mp4" type="video/mp4">
</video>

**A web-based object detection system using YOLOv8 and Streamlit**

</div>

## 📋 Table of Contents
- [✨ Features](#-features)
- [🚀 Quick Start](#-quick-start)
- [🏗️ Project Structure](#️-project-structure)
- [🔧 Installation Guide](#-installation-guide)
- [💻 Usage](#-usage)
- [📊 Output Formats](#-output-formats)
- [⚙️ Technical Architecture](#️-technical-architecture)
- [🧠 How It Works](#-how-it-works)
- [🐛 Troubleshooting](#-troubleshooting)

## ✨ Features

### 🖼️ **Image Processing**
- **Multi-format Support**: JPG, PNG, JPEG
- **Original Quality**: Maintains original image resolution
- **User-Friendly Interface**: Simple upload and processing workflow
- **Side-by-Side Comparison**: Original vs processed view

### 🤖 **AI & Detection**
- **YOLOv8 Integration**: Modern object detection architecture
- **Multiple Model Options**:
  - **YOLOv8n** (Nano): Fastest variant (23MB)
  - **YOLOv8s** (Small): Balanced speed/accuracy (87MB)
  - **YOLOv8m** (Medium): Most accurate variant (217MB)
- **COCO Dataset Classes**: Detects 80+ common object categories
- **Automatic Model Download**: Downloads models on first use

### 📊 **Analytics & Reporting**
- **Real-time Object Counting**: Instant detection statistics
- **Confidence Metrics**: Average, minimum, maximum confidence scores
- **Class Distribution Analysis**: Percentage breakdown by object type
- **Bounding Box Data**: Precise coordinates and dimensions
- **Visual Charts**: Interactive class distribution visualization

### 🎨 **User Interface**
- **Modern Streamlit Interface**: Clean, responsive web design
- **Tab-Based Organization**: Logical grouping of features and results
- **Real-Time Processing Feedback**: Live progress indicators
- **Interactive Controls**: Sliders, selectors, and toggle switches
- **Responsive Layout**: Works on desktop and mobile devices

### 💾 **Data Management & Export**
- **Multiple Export Formats**:
  - **Processed Images**: JPG with bounding boxes and labels
  - **Structured CSV Data**: Detection coordinates and metadata
  - **Text Reports**: Formatted statistics summary
- **Session Management**: Maintains state between interactions
- **Batch Processing Ready**: Modular architecture for scaling

## 🚀 Quick Start

### Prerequisites
- **Python 3.8+** (Recommended: Python 3.10 or higher)
- **4GB RAM** minimum (8GB recommended for YOLOv8m)
- **Internet connection** for initial package and model download
- **500MB free disk space** for models and dependencies

### Installation in 3 Minutes
```bash
# 1. Clone or create project folder
mkdir object-detection-app
cd object-detection-app

# 2. Create project structure
mkdir utils
mkdir models
mkdir assets

# 3. Create and install requirements
echo "ultralytics>=8.0.196" > requirements.txt
echo "streamlit>=1.28.0" >> requirements.txt
echo "opencv-python>=4.8.1.78" >> requirements.txt
echo "pandas>=2.1.4" >> requirements.txt
echo "Pillow>=10.1.0" >> requirements.txt

pip install -r requirements.txt
```

### Launch Application
```bash
# Start the Streamlit application
streamlit run app.py

# For custom port (if 8501 is busy):
streamlit run app.py --server.port 8502
```

🌐 **Open browser and navigate to:** `http://localhost:8501`

## 🏗️ Project Structure

```
object-detection-app/
├── app.py                    # Main Streamlit application
├── README.md                 # This documentation file
├── .gitignore               # Git ignore patterns
├── requirements.txt          # Python dependencies
│
├── utils/                   # Core application modules
│   ├── __init__.py
│   ├── detection.py         # YOLOv8 object detection logic
│   └── counting.py          # Statistical analysis functions
│
├── models/                  # YOLO model storage
│
└── assets/                  # Demonstration and resource files
    └── demo.mp4            # MP4 demonstration video
```

## 🔧 Installation Guide

### Complete Setup

#### Step 1: Environment Preparation
```bash
# Navigate to your projects directory
cd ~/Desktop  # or your preferred location

# Create project directory
mkdir object-detection-app
cd object-detection-app

# Create virtual environment (strongly recommended)
python -m venv venv

# Activate virtual environment
# Windows:
venv\Scripts\activate

# Mac/Linux:
source venv/bin/activate
```

#### Step 2: File Structure Creation
```bash
# Create all required directories
mkdir -p utils models assets

# Create essential Python files
touch app.py requirements.txt README.md .gitignore
touch utils/__init__.py utils/detection.py utils/counting.py
```

#### Step 3: Dependencies Installation
```bash
# Install with specific versions for compatibility
pip install --upgrade pip

pip install ultralytics==8.0.196 \
            streamlit==1.28.0 \
            opencv-python==4.8.1.78 \
            pandas==2.1.4 \
            Pillow==10.1.0
```

#### Step 4: Verification
```bash
# Test that all imports work correctly
python -c "
try:
    import streamlit, pandas, cv2
    from PIL import Image
    from ultralytics import YOLO
    print('✅ All imports successful!')
    print(f'Streamlit: {streamlit.__version__}')
    print(f'OpenCV: {cv2.__version__}')
except Exception as e:
    print(f'❌ Import error: {e}')
"
```

## 💻 Usage

### Complete User Guide

#### 1. Application Launch
```bash
# Basic launch
streamlit run app.py

# With verbose logging (for debugging)
streamlit run app.py --logger.level=debug

# With specific host and port
streamlit run app.py --server.port 8502 --server.address 0.0.0.0
```

#### 2. Image Upload Process
1. **Click "Browse files"** in the left sidebar panel
2. **Select an image file** from your computer
3. **Supported formats**:
   - **JPEG/JPG** (Recommended for best performance)
   - **PNG** (Supports transparency)
   - **Maximum size**: 10MB (Streamlit default limit)

#### 3. Model Selection Guide
| Model Variant | Size | Best Use Case | Performance Notes |
|---------------|------|---------------|-------------------|
| **YOLOv8 Nano** | 23MB | Quick testing, mobile deployment | Fastest inference, lower accuracy |
| **YOLOv8 Small** | 87MB | General purpose, balanced needs | Good speed/accuracy balance |
| **YOLOv8 Medium** | 217MB | High accuracy requirements | Best detection quality, slower |

#### 4. Results Analysis Workflow
1. **Image Comparison Tab**:
   - Original image (left)
   - Processed image with bounding boxes (right)
   - Image dimensions and metadata

2. **Detection Details Tab**:
   - Interactive table with all detected objects
   - Sortable columns (class, confidence, size)
   - Filtering capabilities

3. **Statistics Panel**:
   - Object count summary
   - Confidence score distribution
   - Class frequency analysis
   - Image coverage metrics

#### 5. Export Options
```python
# Three export formats available:
1. detection_result.jpg    # Visual result with annotations
2. detection_data.csv      # Structured detection dataset
3. detection_report.txt    # Summary statistics and metrics
```

## 📊 Output Formats

### 1. Processed Image Output (`detection_result.jpg`)
```
File Format: JPEG with embedded annotations
Features:
- Color-coded bounding boxes (different colors per class)
- Object class labels with confidence percentages
- Clean visual presentation suitable for reports
- Maintains original image quality
```

**Example Output Structure:**
```
Image: detection_result.jpg
├── Visual Elements:
│   ├── Bounding Boxes: Rectangles around detected objects
│   ├── Labels: "person: 92%", "car: 88%", etc.
│   ├── Confidence Scores: Displayed with each detection
│   └── Color Coding: Consistent colors for same object classes
└── Technical Specs:
    ├── Format: JPEG
    ├── Quality: 95% (configurable)
    └── Metadata: Preserves original EXIF data
```

### 2. CSV Data Export (`detection_data.csv`)
```csv
class,confidence,x_min,y_min,x_max,y_max,width,height,area,timestamp
person,0.89,100,150,200,350,100,200,20000,2024-01-15 10:30:00
car,0.95,300,200,450,300,150,100,15000,2024-01-15 10:30:00
dog,0.78,50,400,150,500,100,100,10000,2024-01-15 10:30:00
bicycle,0.82,400,300,550,450,150,150,22500,2024-01-15 10:30:00
```

**CSV Column Descriptions:**
- `class`: Detected object category
- `confidence`: Detection confidence (0-1)
- `x_min, y_min`: Top-left bounding box coordinates
- `x_max, y_max`: Bottom-right bounding box coordinates  
- `width, height`: Bounding box dimensions in pixels
- `area`: Bounding box area in pixels²
- `timestamp`: Processing timestamp

### 3. Statistical Report (`detection_report.txt`)
```
========================================
OBJECT DETECTION ANALYSIS REPORT
========================================
Report Generated: 2024-01-15 10:30:00
Image File: sample_image.jpg
Model Used: yolov8s.pt
Image Dimensions: 1920 × 1080 pixels

SUMMARY STATISTICS
========================================
Total Objects Detected: 15
Unique Object Classes: 6
Average Confidence Score: 84.7%
Minimum Confidence: 67.3%
Maximum Confidence: 96.8%

CLASS DISTRIBUTION
========================================
1. person: 5 objects (33.3%)
2. car: 4 objects (26.7%)
3. chair: 2 objects (13.3%)
4. dog: 2 objects (13.3%)
5. bottle: 1 object (6.7%)
6. laptop: 1 object (6.7%)

CONFIDENCE ANALYSIS
========================================
Confidence Range: 67.3% - 96.8%
Mean Confidence: 84.7%
Standard Deviation: 8.2%
High Confidence Detections (>80%): 11 objects (73.3%)

SPATIAL ANALYSIS
========================================
Total Detection Area: 412,500 pixels²
Image Coverage: 19.8% of total area
Average Object Size: 27,500 pixels²
Density: 0.72 objects per 10,000 pixels

DETECTION QUALITY METRICS
========================================
Detection Quality: Good
Recommendation: Results suitable for analysis
========================================
```

## ⚙️ Technical Architecture

### System Architecture Diagram
```
┌─────────────────────────────────────────────────┐
│               USER INTERFACE LAYER              │
├─────────────────────────────────────────────────┤
│  Streamlit Web Application (app.py)             │
│  • File upload and user interaction             │
│  • Results display and visualization            │
│  • Export functionality                         │
└──────────────────────┬──────────────────────────┘
                       │
┌──────────────────────▼──────────────────────────┐
│              PROCESSING LAYER                   │
├─────────────────────────────────────────────────┤
│  Object Detection Module (utils/detection.py)   │
│  • YOLOv8 model initialization and inference    │
│  • Bounding box extraction and annotation       │
│  • Detection data structuring                   │
└──────────────────────┬──────────────────────────┘
                       │
┌──────────────────────▼──────────────────────────┐
│              ANALYTICS LAYER                    │
├─────────────────────────────────────────────────┤
│  Statistics Module (utils/counting.py)          │
│  • Object counting and classification           │
│  • Statistical metric calculation               │
│  • Report generation and formatting             │
└─────────────────────────────────────────────────┘
```

### Code Architecture Details

#### Main Application (`app.py`)
```python
"""
app.py - Primary Streamlit Application
Architecture:
1. Page Configuration & Setup
2. Sidebar User Controls
3. Image Processing Pipeline
4. Results Visualization
5. Export Management
"""
Key Components:
• setup_page_configuration() - UI/UX settings
• create_sidebar() - User input collection
• process_image_file() - Core detection pipeline
• display_results() - Multi-tab results presentation
• Error handling and user feedback
```

#### Detection Module (`utils/detection.py`)
```python
"""
ObjectDetector Class - Core Detection Engine
Responsibilities:
1. YOLOv8 model management and inference
2. Bounding box processing and annotation
3. Detection data extraction and structuring
4. Error handling and model fallbacks
"""
class ObjectDetector:
    def __init__(self, model_name='yolov8n.pt'):
        # Model initialization with error handling
        # Automatic download if model not present
        # Configuration management
    
    def detect_objects(self, image_path):
        # Full detection pipeline:
        # 1. Image loading and preprocessing
        # 2. YOLOv8 inference execution
        # 3. Results processing and annotation
        # 4. Output generation
    
    def get_detection_data(self):
        # Structured data extraction:
        # • Object classes and confidence scores
        # • Bounding box coordinates and dimensions
        # • Metadata and processing information
```

#### Analytics Module (`utils/counting.py`)
```python
"""
Statistical Analysis Module
Functions:
1. count_objects() - Object frequency analysis
2. generate_statistics() - Comprehensive metrics
3. calculate_metrics() - Advanced calculations
4. format_statistics() - Report generation
5. validate_detection_data() - Data quality checks
"""
Key Algorithms:
• Frequency distribution analysis
• Confidence interval calculations
• Spatial coverage computations
• Data validation and sanitization
```

## 🧠 How It Works

### Complete Detection Pipeline

#### Phase 1: Input Processing
```python
# Step 1: Image Upload & Validation
uploaded_file → Streamlit file handler → Format validation → Size check

# Step 2: Temporary File Management
original_image → Temporary storage → Path management → Cleanup scheduling

# Step 3: Image Preprocessing
image_array → Color space conversion → Dimension verification → Quality check
```

#### Phase 2: Model Inference
```python
# Step 1: Model Initialization
model_name → YOLO() constructor → Weight loading → Configuration setup

# Step 2: Forward Pass
image_tensor → YOLOv8 network → Feature extraction → Detection heads

# Step 3: Post-processing
raw_predictions → Confidence thresholding → Non-maximum suppression → Box formatting
```

#### Phase 3: Results Processing
```python
# Step 1: Visualization
detection_boxes → OpenCV drawing → Label placement → Color coding

# Step 2: Data Extraction
box_data → DataFrame conversion → Column formatting → Type casting

# Step 3: Statistical Analysis
detection_df → Count functions → Metric calculations → Report generation
```

#### Phase 4: Output Generation
```python
# Step 1: User Interface Updates
processed_image → Streamlit display → Table rendering → Chart generation

# Step 2: Export Preparation
formatted_data → File encoding → Compression → Download preparation

# Step 3: Session Management
user_state → Cache updating → History logging → Resource cleanup
```

### Key Algorithms and Methods

#### 1. Bounding Box Processing Algorithm
```python
Algorithm: process_bounding_boxes()
Input: Raw YOLOv8 predictions
Output: Structured detection data
Steps:
1. Filter predictions by confidence threshold (default: 0.5)
2. Apply Non-Maximum Suppression (NMS) for overlapping boxes
3. Convert coordinates to pixel values
4. Calculate dimensions and areas
5. Map class IDs to human-readable names
6. Structure data for DataFrame conversion
```

#### 2. Statistical Analysis Algorithm
```python
Algorithm: analyze_detections()
Input: Detection DataFrame
Output: Statistical summary
Steps:
1. Calculate basic counts (total, unique classes)
2. Compute confidence statistics (mean, std, min, max)
3. Generate frequency distribution
4. Calculate spatial metrics (coverage, density)
5. Format results for display and export
```

## 🐛 Troubleshooting

### Common Issues and Solutions

#### Issue 1: Model Download Failures
**Symptoms**: `URLError`, `TimeoutError`, or "Unable to download model"
```bash
# Solution A: Manual Model Download
curl -L https://github.com/ultralytics/assets/releases/download/v0.0.0/yolov8n.pt -o models/yolov8n.pt

# Solution B: Use Local Model Path
# Modify detection.py:
model = YOLO('models/yolov8n.pt')  # Instead of just 'yolov8n.pt'

# Solution C: Offline Mode Preparation
# Download models in advance on a machine with internet
# Then copy models/ folder to offline machine
```

#### Issue 2: Memory Allocation Errors
**Symptoms**: `MemoryError`, slow performance, or system freezing
```python
# Prevention Strategies:
1. Use smaller model: yolov8n.pt instead of yolov8m.pt
2. Resize images before upload:
   from PIL import Image
   img = Image.open(uploaded_file).resize((1024, 768))
3. Clear Streamlit cache:
   streamlit cache clear
4. Close other memory-intensive applications
```

#### Issue 3: Streamlit Connection Issues
**Symptoms**: Cannot connect to `localhost:8501`, port already in use
```bash
# Diagnostic Commands:
# Check port usage (Windows):
netstat -ano | findstr :8501

# Check port usage (Mac/Linux):
lsof -i :8501

# Solutions:
# 1. Use different port:
streamlit run app.py --server.port 8502

# 2. Kill existing process:
# Windows:
taskkill /PID <PID> /F
# Mac/Linux:
kill -9 <PID>
```

#### Issue 4: Package Version Conflicts
**Symptoms**: `ImportError`, `AttributeError`, or incompatible versions
```bash
# Clean Reinstallation:
pip uninstall ultralytics streamlit opencv-python pandas Pillow -y
pip install --no-cache-dir ultralytics==8.0.196 streamlit==1.28.0

# Virtual Environment Recreation:
deactivate
rm -rf venv/
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate
pip install -r requirements.txt
```

#### Issue 5: Image Processing Errors
**Symptoms**: `UnidentifiedImageError`, corrupted images, or format issues
```python
# Validation Code Snippet:
from PIL import Image
import io

def validate_image(file_bytes):
    try:
        img = Image.open(io.BytesIO(file_bytes))
        img.verify()  # Verify it's a valid image
        img = Image.open(io.BytesIO(file_bytes))  # Reopen for use
        return img
    except Exception as e:
        st.error(f"Invalid image file: {str(e)}")
        return None
```

### Performance Optimization Tips

#### For Better Speed:
1. **Use YOLOv8n** for fastest inference
2. **Resize images** to 1024x768 or smaller before upload
3. **Enable GPU** if available (requires CUDA setup)
4. **Use Streamlit caching** for repeated operations

#### For Better Accuracy:
1. **Use YOLOv8m** for highest detection quality
2. **Upload high-resolution images** (1920x1080 or higher)
3. **Ensure good lighting and contrast** in source images
4. **Use appropriate confidence threshold** (adjust in detection.py)

### Debug Mode Activation
```python
# Add to app.py for detailed debugging
DEBUG_MODE = st.sidebar.checkbox("Enable Debug Mode")

if DEBUG_MODE:
    st.write("### Debug Information")
    st.write(f"Uploaded file: {uploaded_file}")
    st.write(f"Selected model: {selected_model}")
    st.write(f"Detection DF shape: {detection_df.shape if detection_df is not None else 'None'}")
```

## 📈 Performance Guidelines

### Expected Performance Metrics
| Hardware Setup | YOLOv8n | YOLOv8s | YOLOv8m |
|----------------|---------|---------|---------|
| CPU (i5/i7) | 50-100ms | 100-200ms | 200-400ms |
| GPU (GTX 1060+) | 10-20ms | 20-40ms | 40-80ms |
| Memory Usage | 1-2GB | 2-3GB | 3-4GB |

### Quality vs Speed Trade-offs
- **For real-time applications**: Use YOLOv8n with resized images
- **For analysis and reports**: Use YOLOv8m with full-resolution images
- **For general use**: YOLOv8s provides the best balance

---

<div align="center">

## 🎓 Academic Project - Group 9

**Object Detection System with YOLOv8 and Streamlit**

### ✅ Project Completion Checklist
- [x] Full object detection functionality
- [x] Multi-model support (nano, small, medium)
- [x] Comprehensive statistical analysis
- [x] Multiple export formats (JPG, CSV, TXT)
- [x] Complete documentation
- [x] Error handling and user feedback
- [x] Demonstration materials (GIF, screenshots)
- [x] Code optimization and cleanup

### 📞 Contact & Support
For questions or issues with this project, please contact the development team or refer to the troubleshooting section above.

---

**🎯 "Seeing the unseen through computer vision"**

</div>
