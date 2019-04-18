import configparser
import json
import os
import requests


class Movie:
    """Movie properties: 
        imdb_id (str): The identifier for the movie from imdb.com
        trailer_youtube_url (str): The URL to the YouTube movie trailer.
        title (str): The title of the movie.
        year (str): The year the movie was released.
        rated (str): The rating of the movie
        poster_image_url (str): The URL to the image of the movie poster.
    """

    def __init__(self, imdb_id, trailer_youtube_url, title='', year='',
                 rated='', poster_image_url=''):
        self.imdb_id = imdb_id
        self.trailer_youtube_url = trailer_youtube_url
        self.title = title
        self.year = year
        self.rated = rated
        self.poster_image_url = poster_image_url


class EntertainmentCenter:
    """ Example metadata representing media in an entertainment center."""

    def __init__(self):
        # Create Movie instances from hard coded data
        m1 = Movie(imdb_id='tt0097958',
                   trailer_youtube_url='https://www.youtube.com/watch?v=tLVd4ipC5Lc')
        m2 = Movie(imdb_id='tt0072431',
                   trailer_youtube_url='https://www.youtube.com/watch?v=mOPTriLG5cU')
        m3 = Movie(imdb_id='tt0071853',
                   trailer_youtube_url='https://www.youtube.com/watch?v=LG1PlkURjxE')
        m4 = Movie(imdb_id='tt0107290',
                   trailer_youtube_url='https://www.youtube.com/watch?v=Bim7RtKXv90')
        m5 = Movie(imdb_id='tt0087182',
                   trailer_youtube_url='https://www.youtube.com/watch?v=abiR2ngzVkM')
        m6 = Movie(imdb_id='tt0114709',
                   trailer_youtube_url='https://www.youtube.com/watch?v=KYz2wyBy3kc')
        m7 = Movie(imdb_id='tt0094625',
                   trailer_youtube_url='https://www.youtube.com/watch?v=NCmVrn2gnRs')
        m8 = Movie(imdb_id='tt0266697',
                   trailer_youtube_url='https://www.youtube.com/watch?v=7kSuas6mRpk')
        m9 = Movie(imdb_id='tt0378194',
                   trailer_youtube_url='https://www.youtube.com/watch?v=NSR7xRGBnOE')
        self.movies = [m1, m2, m3, m4, m5, m6, m7, m8, m9]

        # Load movie data from external source: omdb api
        self.load_movie_data_from_omdb()

    def load_movie_data_from_omdb(self):
        """
        Populates data in the movies attribute by calling OMDB API and
        passing in the imdb_id if present.
        """

        # Load OMDB API Key from external config
        config = configparser.ConfigParser()
        config.read(os.path.join(
            os.path.join(os.path.abspath(os.path.dirname(__file__)), 'config.ini')))
        omdb_api_key = config['DEFAULT']['omdb.api.key']

        # Retrieve Movie Data
        get_movie_url = 'http://www.omdbapi.com'

        for movie in self.movies:
            if movie.imdb_id:
                params = {'apikey': omdb_api_key, 'i': movie.imdb_id}
                response = requests.get(get_movie_url, params=params)
                data = json.loads(response.text)
                if response.status_code == 200 and 'Error' not in data:
                    movie.title = data.get('Title', '')
                    movie.year = data.get('Year', '')
                    movie.rated = data.get('Rated', '')
                    movie.poster_image_url = data.get('Poster', '')
                else:
                    print("Fetching movie info for imdb id ({}) resulted in an" " error {}. {}".format(
                        movie.imdb_id, response.status_code, data.get('Error', 'Unspecified error')))
