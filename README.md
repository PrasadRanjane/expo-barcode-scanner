# Barcode & QR Scanner Component

A professional, feature-rich barcode and QR code scanner component for React Native using Expo. Features a modern UI, smooth animations, and comprehensive scanning capabilities.

## Features

- ✅ **QR Code Scanning** - Scan QR codes instantly
- ✅ **Barcode Support** - Multiple barcode formats (Code128, Code39, EAN13, EAN8, UPC)
- ✅ **Modern UI** - Fresh color scheme with dark theme
- ✅ **Smooth Animations** - Animated scan line and data display
- ✅ **Permission Handling** - Graceful camera permission requests
- ✅ **Smart Detection** - Auto-detects URLs, emails, and phone numbers
- ✅ **Action Buttons** - Quick actions for detected content types
- ✅ **Visual Feedback** - Clear scanning frame with corner indicators

## Installation in Expo Snack

1. Copy all files to your Snack
2. Dependencies will be automatically installed:
   - `expo-camera` (barcode scanning functionality)
   - `@expo/vector-icons`
3. Run!

## Usage

```tsx
import { CameraView, useCameraPermissions } from 'expo-camera';

const [permission, requestPermission] = useCameraPermissions();
const [scanned, setScanned] = useState(false);

useEffect(() => {
  if (permission === null) {
    requestPermission();
  }
}, [permission, requestPermission]);

const handleBarCodeScanned = ({ type, data }) => {
  setScanned(true);
  console.log('Scanned:', type, data);
};

return (
  <CameraView
    onBarcodeScanned={scanned ? undefined : handleBarCodeScanned}
    barcodeScannerSettings={{
      barcodeTypes: ['qr', 'code128', 'code39'],
    }}
    style={StyleSheet.absoluteFillObject}
  />
);
```

## Supported Barcode Types

- QR Code
- Code 128
- Code 39
- EAN-13
- EAN-8
- UPC

## Features Breakdown

### Scanner Overlay
- Animated scanning line
- Corner indicators
- Dark overlay with transparent scan area
- Visual feedback during scanning

### Scanned Data Display
- Slide-up animation
- Type detection (QR, Barcode)
- Smart content detection (URL, Email, Phone)
- Quick action buttons
- Copy and share functionality

### Permission Handling
- Automatic permission requests
- Clear error messages
- Settings redirect
- Retry functionality

## Color Scheme

- **Primary**: #6366f1 (Indigo)
- **Secondary**: #10b981 (Emerald)
- **Background**: #0f172a (Dark Slate)
- **Surface**: #1e293b (Slate)
- **Text**: #f1f5f9 (Light Slate)

## Platform Support

- ✅ iOS
- ✅ Android
- ⚠️ Web (limited support)

## Permissions

The app requires camera permission to function. Permissions are requested automatically on first launch.

### iOS
Add to `app.json`:
```json
{
  "ios": {
    "infoPlist": {
      "NSCameraUsageDescription": "This app needs camera access to scan codes."
    }
  }
}
```

### Android
Add to `app.json`:
```json
{
  "android": {
    "permissions": ["CAMERA"]
  }
}
```

## Example Snack

See `App.tsx` for complete implementation with all features.

## License

Free to use in your projects!
