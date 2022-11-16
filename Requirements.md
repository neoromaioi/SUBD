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
    - FirstName - varchar(user first name)
    - LastName - varchar(user last name)
    - Password - varchar(user password)
    - Email - varchar(user email)
    - Blocked - bool(is the user blocked or not) 
____
- Role - roles for users

    - **RoleID** - uuid
    - Name - varchar(role name)
____
- Log - user action logs

    - **UserID** - uuid(foreign key)
    - Info - varchar(user action for log)
    - Date - time(time of user action)
____
- Review - book review

    - **ReviewID** - uuid
    - BookID - uuid(foreign key)
    - Text - varchar(book review text)
    - User - uuid(IdUser, one to one review user)
____
- Rating - book rating

    - **RatingID** - uuid
    - BookID - uuid(foreign key)
    - Mark - int(book rating from 1 to 10)
    - User - uuid(IdUser, one to one rating user)
____
- Book

    - **BookID** - uuid
    - Description - varchar(book description)
    - PublishingHouse - time(book publishing house)
    - Series - varchar(book series)
    - Year - int(book release year)
    - Cover - varchar(book cover image path)
    - Pages - int(book pages)
    - Size - varchar(book size)
    - ISBN - varchar(book ISBN number)
____
- Authors - many to many table between Book and Author

    - **AuthorID** - uuid(foreign key)
    - **BookID** - uuid(foreign key)
____
- BookGenre - many to many table between Book and Genre

    - **GenreID** - uuid(foreign key)
    - **BookID** - uuid(foreign key)
____
- Genre - book genre

    - **GenreID** - uuid
    - Name - varchar(genre name)
____
- Author - book author

    - **AuthorID** - uuid
    - Name - varchar(author name)
    - BirthDate - int(authors birth date)
    - DeathDate - int(authors death date)
    - Description - varchar(author description)
    - Image - varchar(author image image path)
____
Normalized database:
![normalized database](https://github.com/neoromaioi/SUBD/raw/main/Picture2.png)