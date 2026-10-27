# Anime Shorts Board

A two-person agile board for making a vertical anime short series: 26 two-week sprints, outsourcing monitor, printable sticker sheet and wall board.

Open `index.html` in a browser to use it. With no setup it saves in that browser only. Use **Export backup** and **Import** to move it between computers.

## 1. Put it on GitHub

1. Create a new repository on github.com (for free GitHub Pages it must be **public**).
2. Click **Add file > Upload files**, drag in `index.html`, `config.js` and `README.md`, and commit.

## 2. Turn on the website

1. In the repository go to **Settings > Pages**.
2. Under **Build and deployment**, choose **Deploy from a branch**, branch `main`, folder `/ (root)`, and save.
3. After a minute the board is live at `https://<your-username>.github.io/<repository-name>/`.

## 3. Share one board between both of you (optional, free)

1. Go to console.firebase.google.com, create a project, then add a **Web app** and copy its config.
2. Open **Build > Firestore Database** and create a database.
3. In the **Rules** tab, paste this and publish. It lets anyone who knows your secret board id read and change that one document, and nothing else:

   ```
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /boards/{id} {
         allow get, create, update: if true;
       }
     }
   }
   ```
4. Edit `config.js` on GitHub: set `boardId` to a long random string only you two know, and paste the Firebase config into `firebase`.
5. Open the site. The status line shows **Shared board · live**.

The first person to open the site after this uploads their board. Keep the website address and `boardId` private. Anyone who has both can edit the board.
