# Google Drive Integration Setup Guide

## Fixing "redirect_uri_mismatch" Error

The error you're seeing occurs because the redirect URI in your Google Cloud Console doesn't match what the application is sending.

### Step 1: Go to Google Cloud Console
1. Visit https://console.cloud.google.com/
2. Select your project (or create a new one)
3. Go to "APIs & Services" > "Credentials"

### Step 2: Update OAuth 2.0 Client ID
1. Find your OAuth 2.0 Client ID (the one used in your .env file)
2. Click on it to edit
3. In "Authorized JavaScript origins", add:
   - `http://localhost:3000`
4. In "Authorized redirect URIs", add:
   - `http://localhost:3000`
5. Click "Save"

### Step 3: Enable Required APIs
Make sure these APIs are enabled:
1. Google Drive API
2. Google Picker API

### Step 4: Restart Development Server
After making changes, restart your React development server:
```bash
cd frontend
npm start
```

## How It Works Now

The updated Google Drive integration now:

1. **Modern Authentication**: Uses Google Identity Services (GIS) instead of deprecated gapi.auth
2. **Proper Redirect URI**: Uses http://localhost:3000 as the redirect URI
3. **Better Error Handling**: Provides user-friendly error messages
4. **Image Filtering**: Only shows image files (JPEG, PNG, GIF, WebP)
5. **iLovePDF-like UX**: Similar authentication flow to iLovePDF

## Testing

1. Go to http://localhost:3000
2. Navigate to User Dashboard
3. Click "+ New Complaint"
4. Select "Google Drive" for photo upload
5. Click "Pick from Google Drive"
6. You should now see the Google sign-in flow working properly

## Troubleshooting

If you still see errors:
1. Double-check the redirect URIs in Google Cloud Console (must be http://localhost:3000)
2. Ensure the Client ID matches exactly what's in your .env file
3. Make sure both APIs (Drive API and Picker API) are enabled
4. Clear your browser cache and cookies
