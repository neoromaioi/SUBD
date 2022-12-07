1. User roles:
+ default
+ moderator
+ admin
- Default user:
    - authentification
    - leave a review for the book
    - rate the book
- Moderator:
    - delete reviews
    - edit and add books, authors
- Admin:
    - same as moderator and block user
____
Database diagram:
![unnormalized database](https://github.com/neoromaioi/SUBD/raw/main/Picture1.png)


Database description:

**Highlighted** fields are primary keys or part of them

- User - all users

    - **UserID** - uuid
    - RoleID - uuid(foreign key)
    - Name - varchar(32)(user login)
    - FirstName - varchar(32)(user first name)
    - LastName - varchar(32)(user last name)
    - Password - varchar(64)(user password)
    - Email - varchar(64)(user email)
    - Blocked - bool(is the user blocked or not) 
____
- Role - roles for users

    - **RoleID** - uuid
    - Name - varchar(10)(role name)
____
- Log - user action logs

    - **UserID** - uuid(foreign key)
    - Info - varchar(128)(user action for log)
    - Date - datetime(time of user action)
____
- Review - book review

    - **UserID** - uuid(foreign key)
    - **BookID** - uuid(foreign key)
    - Text - varchar(1024)(book review text)
    - User - uuid(IdUser, one to one review user)
____
- Rating - book rating

    - **UserID** - uuid(foreign key)
    - **BookID** - uuid(foreign key)
    - Mark - tinyint(book rating from 1 to 10)(check Mark>0 Mark<11)
    - User - uuid(IdUser, one to one rating user)
____
- Book

    - **BookID** - uuid
    - Description - varchar(1024)(book description)
    - PublishingHouse - varchar(64)(book publishing house)
    - Series - varchar(64)(book series)
    - Year - varchar(32)(book release year)
    - Cover - varchar(256)(book cover image path)
    - Pages - smallint(book pages)
    - Size - varchar(64)(book size)
    - ISBN - varchar(64)(book ISBN number)
____
- BookAuthor - many to many table between Book and Author

    - **AuthorID** - uuid(foreign key)
    - **BookID** - uuid(foreign key)
____
- BookGenre - many to many table between Book and Genre

    - **GenreID** - uuid(foreign key)
    - **BookID** - uuid(foreign key)
____
- Genre - book genre

    - **GenreID** - uuid
    - Name - varchar(64)(genre name)
____
- Author - book author

    - **AuthorID** - uuid
    - Name - varchar(50)(author name)
    - BirthDate - date(authors birth date)
    - DeathDate - date(authors death date)
    - Description - varchar(1024)(author description)
    - Image - varchar(256)(author image path)
____
Normalized database:
![normalized database](https://github.com/neoromaioi/SUBD/raw/main/Picture2.png)