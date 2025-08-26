# OAuth2 Google პროექტის დაყენება / OAuth2 Google Project Setup

---

## 🇬🇪 ქართული ვერსია / Georgian Version

### 1. Google OAuth2 Credentials-ის მიღება

1. გადადით [Google Cloud Console](https://console.cloud.google.com/)
2. შექმენით ახალი პროექტი ან აირჩიეთ არსებული
3. ჩართეთ Google+ API და Google Drive API
4. Credentials > Create Credentials > OAuth 2.0 Client IDs
5. Application type: Web application
6. Authorized redirect URIs: `http://localhost:8000/auth/google/callback`

## 2. Environment Variables

შექმენით `backend/.env` ფაილი:

```env
OAUTH_GOOGLE_CLIENT_ID=your_client_id_here
OAUTH_GOOGLE_CLIENT_SECRET=your_client_secret_here
```

## 3. Backend გაშვება

```bash
cd backend
pip install -r requirements.txt
uvicorn main:app --reload --port 8000
```

## 4. Frontend გაშვება

```bash
cd frontend
npm install
npm run dev
```

## 5. გამოყენება

1. გახსენით `http://localhost:5173`
2. დააჭირეთ "Войти через Google" ღილაკს
3. გაიარეთ Google-ის ავტორიზაცია
4. ნახავთ თქვენს Google Drive ფაილებს

## 6. API დოკუმენტაცია

Backend-ის API endpoints-ის ნახვისთვის:

- **Swagger UI**: `http://localhost:8000/docs` - ინტერაქტიული API დოკუმენტაცია
- **ReDoc**: `http://localhost:8000/redoc` - ალტერნატიული დოკუმენტაცია
- **OpenAPI JSON**: `http://localhost:8000/openapi.json` - API სქემა JSON ფორმატში

### API Endpoints:

- `GET /auth/google/url` - Google OAuth redirect URL-ის მიღება
- `POST /auth/google/callback` - Google OAuth callback-ის დამუშავება

## პრობლემების გადაჭრა

- **CORS Error**: შეამოწმეთ, რომ backend 8000 პორტზეა, frontend 5173-ზე
- **Invalid redirect URI**: შეამოწმეთ Google Console-ში redirect URI
- **State parameter error**: გადატვირთეთ გვერდი და სცადეთ თავიდან

---

## 🇺🇸 English Version

### 1. Getting Google OAuth2 Credentials

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select an existing one
3. Enable Google+ API and Google Drive API
4. Credentials > Create Credentials > OAuth 2.0 Client IDs
5. Application type: Web application
6. Authorized redirect URIs: `http://localhost:8000/auth/google/callback`

### 2. Environment Variables

Create a `backend/.env` file:

```env
OAUTH_GOOGLE_CLIENT_ID=your_client_id_here
OAUTH_GOOGLE_CLIENT_SECRET=your_client_secret_here
```

### 3. Running Backend

```bash
cd backend
pip install -r requirements.txt
uvicorn main:app --reload --port 8000
```

### 4. Running Frontend

```bash
cd frontend
npm install
npm run dev
```

### 5. Usage

1. Open `http://localhost:5173`
2. Click "Войти через Google" button
3. Complete Google authentication
4. View your Google Drive files

### 6. API Documentation

To view backend API endpoints:

- **Swagger UI**: `http://localhost:8000/docs` - Interactive API documentation
- **ReDoc**: `http://localhost:8000/redoc` - Alternative documentation
- **OpenAPI JSON**: `http://localhost:8000/openapi.json` - API schema in JSON format

#### API Endpoints:

- `GET /auth/google/url` - Get Google OAuth redirect URL
- `POST /auth/google/callback` - Handle Google OAuth callback

### Troubleshooting

- **CORS Error**: Check that backend is on port 8000, frontend on 5173
- **Invalid redirect URI**: Verify redirect URI in Google Console
- **State parameter error**: Reload the page and try again
