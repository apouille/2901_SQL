

********************** THE HACKING BLOG *******************************

CREATE TABLE 'users' ('id' INTEGER PRIMARY KEY AUTOINCREMENT,'name' TEXT);

CREATE TABLE 'tags' ('id' INTEGER PRIMARY KEY AUTOINCREMENT,'tag' TEXT,'color' TEXT);

CREATE TABLE 'categories' ('id' INTEGER PRIMARY KEY AUTOINCREMENT,'title' TEXT);

CREATE TABLE 'articles' ('id' INTEGER PRIMARY KEY AUTOINCREMENT,'content' TEXT, 'user_id' INTEGER,FOREIGN KEY(user_id) REFERENCES users(id));

CREATE TABLE 'articles_category' ('id' INTEGER PRIMARY KEY AUTOINCREMENT, 'article_id' INTEGER,'category_id' INTEGER, FOREIGN KEY(article_id) REFERENCES artices(id), FOREIGN KEY(category_id) REFERENCES categories(id));

CREATE TABLE 'tag_category' ('id' INTEGER PRIMARY KEY AUTOINCREMENT,'category_id' INTEGER, 'tag_id' INTEGER, FOREIGN KEY(category_id) REFERENCES categories(id), FOREIGN KEY(tag_id) REFERENCES tags(id));


********************** THE HACKING ACADEMY *****************************

CREATE TABLE 'courses' ('id' INTEGER PRIMARY KEY AUTOINCREMENT,'title' TEXT, 'description' TEXT);

CREATE TABLE 'categories' ('id' INTEGER PRIMARY KEY AUTOINCREMENT,'course_id' INTEGER, 'title' TEXT,'body' TEXT, FOREIGN KEY(course_id) REFERENCES courses(id));



********************** THE HACKING PINTEREST **************************

CREATE TABLE 'users' ('id' INTEGER PRIMARY KEY AUTOINCREMENT,'name' TEXT);

CREATE TABLE 'pictures' ('id' INTEGER PRIMARY KEY AUTOINCREMENT, 'user_id' INTEGER, 'url' TEXT, FOREIGN KEY(user_id) REFERENCES users(id));

CREATE TABLE 'comments' ('id' INTEGER PRIMARY KEY AUTOINCREMENT,'picture_id' INTEGER,
'user_id' INTEGER,'comment' TEXT, FOREIGN KEY(picture_id) REFERENCES pictures(id), FOREIGN KEY(user_id) REFERENCES users(id));


********************** THE HACKING NEWS *******************************

CREATE TABLE `user` (`id` INTEGER PRIMARY KEY AUTOINCREMENT, `name` TEXT);

CREATE TABLE `links` (`id` INTEGER PRIMARY KEY AUTOINCREMENT, `id_user` INTEGER, `url` TEXT, FOREIGN KEY (id_user) REFERENCES user(id));

CREATE TABLE `commentaires` (`id` INTEGER PRIMARY KEY AUTOINCREMENT, `id_links` INTEGER, `id_user` INTEGER, `Contenu` TEXT,  FOREIGN KEY (id_links) REFERENCES links(id), FOREIGN KEY (id_user) REFERENCES user(id));

CREATE TABLE `subcommentaires` (`id` INTEGER PRIMARY KEY AUTOINCREMENT, `id_commentaires` INTEGER, `id_user` INTEGER, `Contenu` TEXT, FOREIGN KEY (id_commentaires) REFERENCES commentaires(id), FOREIGN KEY (id_user) REFERENCES user(id));


********************** THE HACKING CLASS *******************************

CREATE TABLE `lessons` (`id` INTEGER PRIMARY KEY AUTOINCREMENT, `name` TEXT);

CREATE TABLE `student` (`id` INTEGER PRIMARY KEY AUTOINCREMENT, `id_lessons` INTEGER, FOREIGN KEY (id_lessons) REFERENCES lessons(id));