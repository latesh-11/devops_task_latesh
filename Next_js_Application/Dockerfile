FROM node:16
COPY package*.json ./
RUN npm install
COPY . .
ENV NEXT_PUBLIC_FIREBASE_API_KEY=your-firebase-api-key
ENV NEXT_PUBLIC_FIREBASE_PROJECT_ID=your-firebase-project-id
ENV NEXT_PUBLIC_FIREBASE_APP_ID=your-firebase-app-id
RUN npm run build
EXPOSE 3000
CMD ["npm", "start"]
