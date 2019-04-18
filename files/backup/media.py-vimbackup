class Movie:
    """Movie contains properties for movie objects.

    Attributes:
        imdb_id (str): The identifier for the movie from imdb.com
        trailer_youtube_url (str): The URL to the YouTube movie trailer.
        title (str): The title of the movie.
        year (str): The year the movie was released.
        rated (str): The rating of the movie
        poster_image_url (str): The URL to the image of the movie poster.
    """

    def all_properties_non_empty(self):
        """
        Checks to see if all properties are non-empty.
        :return: boolean indicating if all properties are non empty
        (True) or not (False)
        """
        return self.imdb_id and \
               self.trailer_youtube_url and \
               self.title and \
               self.year and \
               self.rated and \
               self.poster_image_url

    def __init__(self, imdb_id, trailer_youtube_url, title='', year='',
                 rated='', poster_image_url=''):
        self.imdb_id = imdb_id
        self.trailer_youtube_url = trailer_youtube_url
        self.title = title
        self.year = year
        self.rated = rated
        self.poster_image_url = poster_image_url
