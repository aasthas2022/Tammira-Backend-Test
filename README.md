# Sample Blog Application

This is a backend application for managing blogs and users using Node.js, Express, MongoDB, and Mongoose.

## Getting Started

To get started, clone the repository and run `npm install` to install the required dependencies.

### Prerequisites

You'll need to have Node.js and MongoDB installed on your machine.

### Installing

To install the dependencies, run:

npm i

### Running the Application

To start the application, run:

npm run start

## API Documentation (ToDo: Create a swagger yml file and move it there)

The following endpoints are available:

### Livecheck (Not expected as per requirement, but added myself for easier debugging - Can be ignored)

GET /livecheck

![livecheck](ImagesForReadme.md/livecheck.png 'GET /livecheck')

### Add a Blog (Not expected as per requirement, but added myself for easier debugging - Can be ignored)

POST /api/blogs

This endpoint adds a new blog. It takes a request body with the following fields:

Example

```json
{
  "title": "Example Blog Post-213213",
  "sub_title": "A Subtitle for the Example Blog Post",
  "content": "Test Content",
  "slug": "example-blog-pos-1t",
  "tags": ["example", "blog", "post"],
  "author": {
    "first_name": "Aastha",
    "last_name": "Shukla",
    "bio": "Actively looking for Summer 2023 Internships in USA/India | MSCS @ Syracuse University| Ex-Senior Software Engineer",
    "profile_pic_url": "https://example.com/profile-pic.jpg"
  }
}
```

The response is the added blog object:

![/api/blogs](ImagesForReadme.md/post_blog_sucessful.png 'POST /api/blogs sucess')

![/api/blogs](ImagesForReadme.md/post_blog_sucessful_mongodb.png '/api/blogs success mongodbview')

### Add a User (Not expected as per requirement, but added myself for easier debugging - Can be ignored)

POST /api/users

This endpoint adds a new user. It takes a request body with the following fields:

```json
{
  "first_name": "Aastha",
  "last_name": "Shukla",
  "email": "AasthaShukla@example.com",
  "password": "password",
  "bio": "Actively looking for Summer 2023 Internships in USA/India | MSCS @ Syracuse University| Ex-Senior Software Engineer",
  "profile_pic_url": "https://example.com/profile.jpg"
}
```

The response is the added user object:

```json
{
  "first_name": "Aastha",
  "last_name": "Shukla",
  "email": "AasthaShukla@example.com",
  "password": "password",
  "bio": "Actively looking for Summer 2023 Internships in USA/India | MSCS @ Syracuse University| Ex-Senior Software Engineer",
  "profile_pic_url": "https://example.com/profile.jpg",
  "_id": "63fee39194dd4e0804f47a17",
  "__v": 0
}
```

![/api/users](ImagesForReadme.md/post_user_sucessful.png 'POST /api/users sucess')

![/api/users](ImagesForReadme.md/post_users_sucessful_mongodb.png '/api/users success mongodbview')

### List blogs with pagination

\*\* GET /api/blogs

This endpoint lists blogs with pagination. It takes two query parameters:

- `page` (optional, default: 1) - the page number to return
- `limit` (optional, default: 10) - the number of blogs per page

The response is an array of blog objects:

```json
{
  "totalCount": 2,
  "results": [
    {
      "author": {
        "first_name": "Aastha",
        "last_name": "Shukla",
        "bio": "Actively looking for Summer 2023 Internships in USA/India | MSCS @ Syracuse University| Ex-Senior Software Engineer",
        "profile_pic_url": "https://example.com/profile-pic.jpg"
      },
      "_id": "63fee37494dd4e0804f47a15",
      "title": "Example Blog Post-213213-2",
      "sub_title": "A Subtitle for the Example Blog Post",
      "content": "Test Content",
      "slug": "example-blog-pos-2",
      "tags": ["example", "blog", "post"],
      "created_date": "2023-03-01T05:32:36.131Z",
      "modified_date": "2023-03-01T05:32:36.131Z",
      "__v": 0
    }
    // More Blogs object
  ]
}
```

![/api/blogs](ImagesForReadme.md/get_api_blogs_success.png 'GET /api/blogs success')

### Get blog by tags

GET /api/blogs/tags/:tag

This endpoint gets blogs by tags. It takes one URL parameter:

- `tag` (required) - the tag to filter by

The response is an array of blog objects:

```json
[
  {
    "author": {
      "first_name": "Aastha",
      "last_name": "Shukla",
      "bio": "Actively looking for Summer 2023 Internships in USA/India | MSCS @ Syracuse University| Ex-Senior Software Engineer",
      "profile_pic_url": "https://example.com/profile-pic.jpg"
    },
    "_id": "63fee2aa94dd4e0804f47a11",
    "title": "Example Blog Post-213213",
    "sub_title": "A Subtitle for the Example Blog Post",
    "content": "Test Content",
    "slug": "example-blog-pos-1t",
    "tags": ["example", "blog", "post"],
    "created_date": "2023-03-01T05:29:14.784Z",
    "modified_date": "2023-03-01T05:29:14.784Z",
    "__v": 0
  }
  // More blog objects
]
```

![/api/blogs/tags/:tag](ImagesForReadme.md/get_api_blogs_by_tags_success.png 'GET /api/blogs/tags/:tag success')

### Update blog by ID

PATCH /api/blogs/:id

This endpoint updates a blog by ID. It takes one URL parameter:

- `id` (required) - the ID of the blog to update

The response shall be:

```json
{
  "author": {
    "first_name": "Aastha-NameUpdated-To-Test", // This is updated for example
    "last_name": "Shukla",
    "bio": "Actively looking for Summer 2023 Internships in USA/India | MSCS @ Syracuse University| Ex-Senior Software Engineer",
    "profile_pic_url": "https://example.com/profile-pic.jpg"
  },
  "_id": "63fee2aa94dd4e0804f47a11",
  "title": "Example Blog Post-213213",
  "sub_title": "A Subtitle for the Example Blog Post",
  "content": "Test Content",
  "slug": "example-blog-pos-1t",
  "tags": ["example", "blog", "post"],
  "created_date": "2023-03-01T05:29:14.784Z",
  "modified_date": "2023-03-01T05:29:14.784Z",
  "__v": 0
}
```

![/api/blogs/:id](ImagesForReadme.md/patch_api_by_id_blogs.png 'GET /api/blogs/:id success')

![/api/blogs/:id](ImagesForReadme.md/patch_api_by_id_blogs_mongodb_success.png 'GET /api/blogs/:id success mongodb_view')

# TODO (Future Score):

- Add swagger.yml file
- Add unit test cases for each .js file
- Add integration test cases
- Update .prettierrc
- Add field validations
- Add route validations
- Add gitlab yml file (for pipelining)
