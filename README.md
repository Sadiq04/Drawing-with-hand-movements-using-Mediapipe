# Gesture-Based Drawing Application

A real-time gesture-controlled drawing application using MediaPipe hand tracking. This project allows users to draw on a virtual canvas using hand gestures, with features like color selection, brush thickness adjustment, and an eraser tool.

## Features

- Real-time hand gesture recognition using MediaPipe
- Virtual drawing canvas with multiple colors
- Adjustable brush thickness
- Eraser tool
- Clean canvas option
- Visual feedback for gesture detection
- Interactive UI elements
- Notification system for user actions

## Requirements

- Python 3.x
- OpenCV (`cv2`)
- MediaPipe
- NumPy
- IPython (for Jupyter Notebook implementation)
- PIL (Python Imaging Library)

To install the required packages:

```bash
pip install opencv-python mediapipe numpy pillow ipython
```

Or: 

```bash
pip install -r requirements.txt
```

## Gesture Controls

The application recognizes several hand gestures for different drawing operations:

1. **Cursor Control**: 
   - Point with index finger to control the cursor
   - Index finger acts as the pointer for UI interaction

2. **Drawing**:
   - Raise both index and middle fingers to enable drawing mode
   - Move your hand to draw on the canvas

3. **UI Interaction**:
   - Point at buttons with index finger
   - Extend thumb while pointing to select/click

4. **Stop Drawing**:
   - Make a fist to stop drawing
   - Lower all fingers to disable drawing mode

## UI Components

The application includes several UI elements:

1. **Color Selection** (Top of screen):
   - Red (default)
   - Yellow
   - Green
   - Blue
   - White
   - Black

2. **Brush Thickness** (Left side):
   - Multiple thickness options (2px, 5px, 8px, 12px)

3. **Tools**:
   - Eraser tool
   - Clean canvas button

## Implementation Details

The application uses MediaPipe's hand tracking module to detect and track 21 hand landmarks in real-time. Key components include:

### Hand Landmark Detection
```python
mp_hands = mp.solutions.hands
hands = mp_hands.Hands()
```

### Gesture Recognition Functions
```python
def is_pointing_finger_up(hand_landmarks):
    index_tip = hand_landmarks.landmark[mp_hands.HandLandmark.INDEX_FINGER_TIP]
    index_mcp = hand_landmarks.landmark[mp_hands.HandLandmark.INDEX_FINGER_MCP]
    return index_tip.y < index_mcp.y

def is_middle_finger_up(hand_landmarks):
    middle_tip = hand_landmarks.landmark[mp_hands.HandLandmark.MIDDLE_FINGER_TIP]
    middle_mcp = hand_landmarks.landmark[mp_hands.HandLandmark.MIDDLE_FINGER_MCP]
    return middle_tip.y < middle_mcp.y
```

### Drawing Parameters
- Canvas size: 480x640 pixels
- Default color: Red (0, 0, 255)
- Default brush thickness: 5px

## Running the Application

1. Clone the repository:
```bash
git clone https://github.com/Sadiq04/Drawing-with-hand-movements-using-Mediapipe.git
```

2. Navigate to the project directory:
```bash
cd gesture-drawing-app
```

3. Run the Jupyter notebook:
```bash
jupyter notebook main.ipynb
```