# Pinterest... but for memes

## Features
- display pictures
- delete pictures
- save memes
- share memes
- organize memes into categories
  - mom approved memees
  - memes for work
  - memes for myself when I have no friends

***

## ***DATABASE***

- users
```sql
CREATE TABLE users (
  user_id SERIAL PRIMARY KEY,
  username VARCHAR(30) NOT NULL,
  profile_pic TEXT DEFAULT 'https://api.time.com/wp-content/uploads/2019/08/mocking_spongebob.jpg',
  email VARCHAR(80) NOT NULL,
  password TEXT NOT NULL
)
```

- memes
```sql
CREATE TABLE memes (
  meme_id SERIAL PRIMARY KEY,
  img_url TEXT NOT NULL,
  category VARCHAR(20),
)
```

- favorites
```sql
CREATE TABLE favorites (
  favorites_id SERIAL PRIMARY KEY,
  meme_id REFERENCES memes(meme_id),
  user_id REFERENCES users(user_id)
)
```

***

## ***SERVER***

### Dependencies
- express
- express-session
- dotenv
- bcryptjs
- massive

### Endpoints
***Authorization***
- login: /auth/login
- register: /auth/register
- logout: /auth/logout
- userSession: /api/user_session

***Meme Controller***
- getMeme: /api/get_memes
- deleteMeme: /api/delete_meme/:memeId
- postMeme: /api/post_meme
- searchByCat: /api/search
- updateMeme: /api/update_category/:memeId

***

## ***CLIENT***
- axios
- redux
- react-redux
- react-router-dom
- http-proxy-middleware
- redux-promise-middleware

### Routes
- login(/login) => home(/)
- profile (/profile)
- account (/account)
- addMeme (/add)

### File-Structure
- src/
  - App.js
  - App.css
  - reset.css
  - index.js
  - components/
    - Login.js
    - Login.css
    - Profile.js
    - Profile.css
    - Home.js
    - Home.css
    - AddMeme.js
    - AddMeme.css
  - redux/
    - reducer
    - store
  - setupProxy.js