
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Librery Management System</title>
    <!-- Bootstrap CSS -->
    <link href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" rel="stylesheet">
    <!-- Custom CSS -->
    <style>
        body {
            background-color: #f8f9fa;
        }

        h1 {
            color: #343a40;
        }

        #articles, #results {
            display: flex;
            flex-wrap: wrap;
            gap: 1rem;
        }
        .font-colo{
            font-size:35px;
            color:red;
        }

        .card {
            width: 100%;
            max-width: 300px; /* Adjust max-width as needed */
        }

        .container {
            padding: 0 15px; /* Adjust for responsive padding */
        }
    </style>
</head>
<body>
    <div class="container mt-5">
        <h1 class="text-center">Librery Management System</h1>
        <div class="row justify-content-center mt-4">
            <div class="col-md-8">
                <div class="input-group mb-3">
                    <input type="text" class="form-control" id="searchInput" placeholder="Search by keywords, categories, or dates">
                    <div class="input-group-append">
                        <button class="btn btn-primary" type="button" onclick="performSearch()">Search</button>
                    </div>
                </div>
            </div>
        </div>

    <!-- jQuery and Bootstrap JS -->
    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.3/dist/umd/popper.min.js"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
    <!-- Custom JS -->
    <script>
        // Expanded list of dummy data
        const articles = [
            { title: 'RBI looks to soften blow of tighter infrastructure funding rules', category: 'Business', date: '2024-08-25' },
            { title: 'FDI inflows surge 26.4% to $22.4 billion in April-June', category: 'Cooruption', date: '2024-07-30' },
            { title: 'Debt-ridden Andhra Pradesh woos investors: Foxconn, Brookfield Corp, Suzlon Energy set to invest in state', category: 'Politics', date: '2024-06-15' },
            { title: 'Finance Ministry says UIDAI does not need to pay income tax', category: 'Tax', date: '2024-08-20' },
            { title: 'One-time UPS allocation wont have big impact on fiscal math', category: 'Schems', date: '2024-08-10' },
            { title: 'DGGI drops ₹3,000 crore tax demand on 18 foreign shipping firms for FY18', category:'Tax', date: '2024-05-05' },
           
        ];

        function displayArticles(articleList) {
            const container = document.getElementById('articles');
            container.innerHTML = '';

            articleList.forEach(article => {
                const articleElement = document.createElement('div');
                articleElement.classList.add('card', 'mb-3');
                articleElement.innerHTML = `
                    <div class="card-body">
                        <h5 class="card-title">${article.title}</h5>
                        <p class="card-text">Category: ${article.category}</p>
                        <p class="card-text">Date: ${article.date}</p>
                    </div>
                `;
                container.appendChild(articleElement);
            });
        }

        function performSearch() {
            const query = document.getElementById('searchInput').value.toLowerCase();
            const resultsContainer = document.getElementById('results');

            // Filter articles based on search query
            const filteredArticles = articles.filter(article => 
                article.title.toLowerCase().includes(query) || 
                article.category.toLowerCase().includes(query) || 
                article.date.includes(query)
            );

            // Clear previous search results
            resultsContainer.innerHTML = '';

            // Display search results
            if (filteredArticles.length > 0) {
                displayArticles(filteredArticles);
            } else {
                resultsContainer.innerHTML = '<p class="text-center">No results found.</p>';
            }
        }

        // Handle Enter key press for search input
        document.getElementById('searchInput').addEventListener('keypress', function(event) {
            if (event.key === 'Enter') {
                event.preventDefault();
                performSearch();
            }
        });

        // Display all articles initially
        document.addEventListener('DOMContentLoaded', () => {
            displayArticles(articles);
        });
    </script>
</body>
</html>
 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Book Library</title>
    <!-- Bootstrap CSS -->
    <link href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" rel="stylesheet">
    <style>
        body {
            background-image: url('https://images.pexels.com/photos/281260/pexels-photo-281260.jpeg?cs=srgb&dl=pexels-francesco-ungaro-281260.jpg&fm=jpg');
            background-size: cover;
            background-position: center;
            color: #fff;
            font-family: Arial, sans-serif;
        }

        header h1 {
            color: #f8f9fa;
            margin-bottom: 30px;
        }

        .book-card {
            background: rgba(0, 0, 0, 0.7);
            border: none;
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .book-card:hover {
            transform: scale(1.05);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
        }

        .card-img-top {
            height: 200px;
            object-fit: cover;
        }

        .btn-info {
            margin-top: 10px;
        }

        .modal-header, .modal-body {
            background: rgba(0, 0, 0, 0.9);
            color: #fff;
        }

        .modal-footer {
            background: rgba(0, 0, 0, 0.7);
        }
    </style>
</head>
<body>
    <div class="container">
        <header class="text-center my-4">
            <h1>Book Library</h1>
        </header>
        <section class="row">
            <!-- Book Cards -->
            <!-- Card 1 -->
            <div class="col-md-4 mb-4">
                <div class="card book-card">
                    <img src="data:image/jpeg;base64,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" class="card-img-top" alt="Book 1">
                    <div class="card-body">
                        <h5 class="card-title">Rich dad poor dad</h5>
                        <p class="card-text">Author: Robert Kiyosaki </p>
                        <button class="btn btn-info" data-toggle="modal" data-target="#book1-modal">More Information</button>
                    </div>
                </div>
            </div>
            <!-- Card 2 -->
            <div class="col-md-4 mb-4">
                <div class="card book-card">
                    <img src="https://images-na.ssl-images-amazon.com/images/S/compressed.photo.goodreads.com/books/1327942880i/2493.jpg" class="card-img-top" alt="Book 2">
                    <div class="card-body">
                        <h5 class="card-title">The Time Machine</h5>
                        <p class="card-text">Author: H.G wells</p>
                        <button class="btn btn-info" data-toggle="modal" data-target="#book2-modal">More Information</button>
                    </div>
                </div>
            </div>
            <!-- Card 3 -->
            <div class="col-md-4 mb-4">
                <div class="card book-card">
                    <img src="https://d28hgpri8am2if.cloudfront.net/book_images/onix/cvr9781398505476/wasteland-9781398505476_lg.jpg" class="card-img-top" alt="Book 3">
                    <div class="card-body">
                        <h5 class="card-title">Waste Land</h5>
                        <p class="card-text">Author: Mary Roach</p>
                        <button class="btn btn-info" data-toggle="modal" data-target="#book3-modal">More Information</button>
                    </div>
                </div>
            </div>
            <!-- Card 4 -->
            <div class="col-md-4 mb-4">
                <div class="card book-card">
                    <img src="https://cdn.kobo.com/book-images/7d80747f-1ab4-4660-a3a9-c8bea08c84b8/353/569/90/False/the-tempest-8.jpg" class="card-img-top" alt="Book 4">
                    <div class="card-body">
                        <h5 class="card-title">The Tempest</h5>
                        <p class="card-text">Author: William Shakespeare</p>
                        <button class="btn btn-info" data-toggle="modal" data-target="#book4-modal">More Information</button>
                    </div>
                </div>
            </div>
            <!-- Card 5 -->
            <div class="col-md-4 mb-4">
                <div class="card book-card">
                    <img src="https://d28hgpri8am2if.cloudfront.net/book_images/onix/cvr9781524879761/the-great-gatsby-9781524879761_lg.jpg" class="card-img-top" alt="Book 5">
                    <div class="card-body">
                        <h5 class="card-title">The Great Gatsby</h5>
                        <p class="card-text">Author: F.Scott Fitzgerald</p>
                        <button class="btn btn-info" data-toggle="modal" data-target="#book5-modal">More Information</button>
                    </div>
                </div>
            </div>
            <!-- Card 6 -->
            <div class="col-md-4 mb-4">
                <div class="card book-card">
                    <img src="https://rukminim2.flixcart.com/image/416/416/jvmpci80/regionalbooks/j/h/s/the-face-of-mother-india-original-imafggugkpynma2n.jpeg?q=70&crop=false" class="card-img-top" alt="Book 6">
                    <div class="card-body">
                        <h5 class="card-title">Mother India</h5>
                        <p class="card-text">Author: Katherine Mayo</p>
                        <button class="btn btn-info" data-toggle="modal" data-target="#book6-modal">More Information</button>
                    </div>
                </div>
            </div>
            <!-- Card 7 -->
            <div class="col-md-4 mb-4">
                <div class="card book-card">
                    <img src="https://cdn.kobo.com/book-images/e382b8f4-2aff-4f68-8a75-aaf669df3e60/353/569/90/False/paradise-lost-204.jpg" class="card-img-top" alt="Book 7">
                    <div class="card-body">
                        <h5 class="card-title">Paradise Lost</h5>
                        <p class="card-text">Author: John Miltion</p>
                        <button class="btn btn-info" data-toggle="modal" data-target="#book7-modal">More Information</button>
                    </div>
                </div>
            </div>
            <!-- Card 8 -->
            <div class="col-md-4 mb-4">
                <div class="card book-card">
                    <img src="https://cdn.kobo.com/book-images/a176250d-66dd-418c-a396-5cde2557c2b7/353/569/90/False/the-descent-of-man-annotated.jpg" class="card-img-top" alt="Book 8">
                    <div class="card-body">
                        <h5 class="card-title">The Descent of Man</h5>
                        <p class="card-text">Author: Charles Darwin</p>
                        <button class="btn btn-info" data-toggle="modal" data-target="#book8-modal">More Information</button>
                    </div>
                </div>
            </div>
            <!-- Card 9 -->
            <div class="col-md-4 mb-4">
                <div class="card book-card">
                    <img src="https://images-na.ssl-images-amazon.com/images/S/compressed.photo.goodreads.com/books/1661015066i/22429484.jpg" class="card-img-top" alt="Book 9">
                    <div class="card-body">
                        <h5 class="card-title">The Wheel of Time</h5>
                        <p class="card-text">Author: Robert Jordan</p>
                        <button class="btn btn-info" data-toggle="modal" data-target="#book9-modal">More Information</button>
                    </div>
                </div>
            </div>
            <!-- Card 10 -->
            <div class="col-md-4 mb-4">
                <div class="card book-card">
                    <img src="https://cdn.kobo.com/book-images/bc66e6da-4181-4208-bd2a-52570c03deb2/353/569/90/False/the-broken-wing.jpg" class="card-img-top" alt="Book 10">
                    <div class="card-body">
                        <h5 class="card-title">The Brokrn Wing</h5>
                        <p class="card-text">Author: Sarojini Naidu</p>
                        <button class="btn btn-info" data-toggle="modal" data-target="#book10-modal">More Information</button>
                    </div>
                </div>
            </div>
            <!-- Card 11 -->
            <div class="col-md-4 mb-4">
                <div class="card book-card">
                    <img src="https://cdn.kobo.com/book-images/3ac03eac-d437-47e3-9b15-52542edabd56/353/569/90/False/war-and-peace-34.jpg" class="card-img-top" alt="Book 11">
                    <div class="card-body">
                        <h5 class="card-title">War And Peace</h5>
                        <p class="card-text">Author: Leo Tolstory</p>
                        <button class="btn btn-info" data-toggle="modal" data-target="#book11-modal">More Information</button>
                    </div>
                </div>
            </div>
            <!-- Card 12 -->
            <div class="col-md-4 mb-4">
                <div class="card book-card">
                    <img src="https://cdn.kobo.com/book-images/164af17b-6987-4165-bfbf-b37c7e84276e/353/569/90/False/the-wealth-of-nations-illustrated-2.jpg" class="card-img-top" alt="Book 12">
                    <div class="card-body">
                        <h5 class="card-title">The Wealth of Nations</h5>
                        <p class="card-text">Author: Adam Smith</p>
                        <button class="btn btn-info" data-toggle="modal" data-target="#book12-modal">More Information</button>
                    </div>
                </div>
            </div>
        </section>
    </div>

    <!-- Modals -->
    <!-- Modal for Book 1 -->
    <div class="modal fade" id="book1-modal" tabindex="-1" role="dialog" aria-labelledby="book1ModalLabel" aria-hidden="true">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="book1ModalLabel">Rich Dad Poor Dad</h5>
                    <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                        <span aria-hidden="true">&times;</span>
                    </button>
                </div>
                <div class="modal-body">
                    <p><strong>Synopsis:</strong>Rich Dad Poor Dad is a 1997 book written by Robert T. Kiyosaki and Sharon Lechter. It advocates the importance of financial literacy, financial independence and building wealth through investing in assets, real estate investing, starting and owning businesses, as well as increasing one's financial intelligence</p>
                    <p><strong>Reviews:</strong>The literary work "Rich Dad Poor Dad," penned by Robert Kiyosaki, is a timeless guide to financial literacy that imparts significant knowledge on capital accumulation and achieving economic autonomy. This written masterpiece has retained its status as an all-time favorite for over twenty years now and continues to be instrumental in empowering countless individuals worldwide towards managing their monetary affairs effectively.</p>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                </div>
            </div>
        </div>
    </div>
    <!-- Modal for Book 2 -->
    <div class="modal fade" id="book2-modal" tabindex="-1" role="dialog" aria-labelledby="book2ModalLabel" aria-hidden="true">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="book2ModalLabel">The Time Machine</h5>
                    <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                        <span aria-hidden="true">&times;</span>
                    </button>
                </div>
                <div class="modal-body">
                    <p><strong>Synopsis:</strong>The Time Machine, first novel by H. G. Wells, published in book form in 1895. The novel is considered one of the earliest works of science fiction and the progenitor of the “time travel” subgenre.</p>
                    <p><Strong>Reviews:</Strong>The Time Traveller Explores This Strange Future World he Uncovers The Unsetting Truth About The Relationship Between The Eloi and The Morlocks Which Serves as Commentary On Social and Class Division.</p>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                </div>
            </div>
        </div>
    </div>
    <!-- Modal for Book 3 -->
    <div class="modal fade" id="book3-modal" tabindex="-1" role="dialog" aria-labelledby="book3ModalLabel" aria-hidden="true">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="book3ModalLabel">Wasteland</h5>
                    <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                        <span aria-hidden="true">&times;</span>
                    </button>
                </div>
                <div class="modal-body">
                    <p><strong>Synopsis:</strong>  wasteland The Economist's 1843 magazine, and many other publications. He is currently the features editor of British GQ.</p>
                    <p><strong>Reviews:</strong> This is an incredible journey into the world of rubbish, full of fascinating characters and mind-bending facts. My relationship with garbage is never going to be the same’ -- Oliver Bullough, author of Moneyland and Butler to the World
                        .</p>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                </div>
            </div>
        </div>
    </div>
    <!-- Modal for Book 4 -->
    <div class="modal fade" id="book4-modal" tabindex="-1" role="dialog" aria-labelledby="book4ModalLabel" aria-hidden="true">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="book4ModalLabel">The Tempest</h5>
                    <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                        <span aria-hidden="true">&times;</span>
                    </button>
                </div>
                <div class="modal-body">
                    <p><strong>Synopsis:</strong> William Shakespeare (1564–1616) was an English poet and playwright who wrote nearly 40 plays and over 150 poems during the Renaissance period.</p>
                    <p><strong>Reviews:</strong> This book is a good book because of its fascinating storyline of a shipwrecked group on a magical island, filled with love, revenge, and forgiveness..</p>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                </div>
            </div>
        </div>
    </div>
    <!-- Modal for Book 5 -->
    <div class="modal fade" id="book5-modal" tabindex="-1" role="dialog" aria-labelledby="book5ModalLabel" aria-hidden="true">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="book5ModalLabel">The Great Gatsby</h5>
                    <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                        <span aria-hidden="true">&times;</span>
                    </button>
                </div>
                <div class="modal-body">
                    <p><strong>Synopsis:</strong> The Great Gatsby by F. Scott Fitzgerald is a classic love story set in the 1920s, in the backdrop of the Jazz Age. The main focus of the plot is the love story between Jay Gatsby and Daisy Buchanan which is set amidst the glittering and decadent social atmosphere.</p>
                    <p><strong>Reviews:</strong> This book is the story of Jay Gatsby, who goes to lavish lengths to win over the love of his life. Or so he thinks. But he doesn’t factor in her husband, his mistress, and his mistress’s husband into the equation. And when he does, there’s everything to keep the story from getting the happy ending that he deserves.</p>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                </div>
            </div>
        </div>
    </div>
    <!-- Modal for Book 6 -->
    <div class="modal fade" id="book6-modal" tabindex="-1" role="dialog" aria-labelledby="book6ModalLabel" aria-hidden="true">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="book6ModalLabel">Mother India</h5>
                    <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                        <span aria-hidden="true">&times;</span>
                    </button>
                </div>
                <div class="modal-body">
                    <p><strong>Synopsis:</strong> Mother India (1927) is a polemical book by American journalist Katherine Mayo on the status of women and girls in Indian society as well as her perception of Hindu culture. The book was translated into more than a dozen languages and reprinted many times in the US.</p>
                    <p><strong>Reviews:</strong> I believe the book does portray India negatively and as Mahatma Gandhi claimed, it is a gutter inspector's report. But, it is not the fault of Ms. Katherine Mayo that the whole country is like a gutter. People can read the book and easily find out what is wrong in India rather than what is wrong with the book.</p>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                </div>
            </div>
        </div>
    </div>
    <!-- Modal for Book 7 -->
    <div class="modal fade" id="book7-modal" tabindex="-1" role="dialog" aria-labelledby="book7ModalLabel" aria-hidden="true">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="book7ModalLabel">Paradise Lost</h5>
                    <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                        <span aria-hidden="true">&times;</span>
                    </button>
                </div>
                <div class="modal-body">
                    <p><strong>Synopsis:</strong> The best well-known work of John Milton (1608-1674), Paradise Lost. A Poem in Ten Books, was first published in London in 1667. In 1674, a new edition was published with some amendments and was divided into the twelve books we are most familiar with now.</p>
                    <p><strong>Reviews:</strong> John Milton's Paradise Lost is one of the greatest epic poems in the English language. It tells the story of the Fall of Man, a tale of immense drama and excitement, of rebellion and treachery, of innocence pitted against corruption, in which God and Satan fight a bitter battle for control of mankind's destiny.</p>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                </div>
            </div>
        </div>
    </div>
    <!-- Modal for Book 8 -->
    <div class="modal fade" id="book8-modal" tabindex="-1" role="dialog" aria-labelledby="book8ModalLabel" aria-hidden="true">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="book8ModalLabel">The Descent of Man</h5>
                    <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                        <span aria-hidden="true">&times;</span>
                    </button>
                </div>
                <div class="modal-body">
                    <p><strong>Synopsis:</strong> Darwin’s (1871) Descent of Man and Selection in Relation to Sex appeared 150 years ago. To commemorate this anniversary, Jeremy DeSilva has edited a volume with an excellent introduction by Janet Browne and ten essays evaluating how well Darwin answered his questions and outlining what has been learned since. The first seven essays deal with the seven chapters of the Descent of Man, the eighth outlines how sexual selection works, the ninth considers chapters 19 and 20 on how sexual selection affected human evolution and racial diversification, and the tenth summarizes fossil and DNA evidence on the rise and fall of hominin diversity .</p>
                    <p><strong>Reviews:</strong>  I like The Descent of Man better than The Origin of Species because Darwin is prepared to be much bolder in The Descent of Man. In The Origin of Species he was still a little bit timid. He presents the idea of how species develop, and that is what we now refer to as evolution. But he didn’t apply it to humans. He really didn’t dare to say that we humans developed from other apes just as horses, for example, developed from early proto-horses. He didn’t use the term ‘evolution’ anywhere in the original editions of The Origin of Species. He does use it in later editions, but that’s around the time when The Descent of Man is published.</p>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                </div>
            </div>
        </div>
    </div>
    <!-- Modal for Book 9 -->
    <div class="modal fade" id="book9-modal" tabindex="-1" role="dialog" aria-labelledby="book9ModalLabel" aria-hidden="true">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="book9ModalLabel">The Wheel of Time</h5>
                    <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                        <span aria-hidden="true">&times;</span>
                    </button>
                </div>
                <div class="modal-body">
                    <p><strong>Synopsis:</strong> Spanning 15 books, released from 1990 to 2013, Robert Jordan was unfortunately only able to complete 11 books and a prequel before his tragic passing, after which Brandon Sanderson took over to finish Jordan’s work, based off the notes he had left behind.</p>
                    <p><strong>Reviews:</strong>  All too often in fantasy writing characters go from being a talentless nobody at the outset of the first story to being an all-powerful, unstoppable force in the span of a single book. However, The Wheel of Time is one of the great outliers and is perhaps the standard bearer in how a power creep can be done wel.</p>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                </div>
            </div>
        </div>
    </div>
    <!-- Modal for Book 10 -->
    <div class="modal fade" id="book10-modal" tabindex="-1" role="dialog" aria-labelledby="book10ModalLabel" aria-hidden="true">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="book10ModalLabel">The Broken Wings</h5>
                    <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                        <span aria-hidden="true">&times;</span>
                    </button>
                </div>
                <div class="modal-body">
                    <p><strong>Synopsis:</strong>  This book was published in early 20th century in 1912. The author has written several books like the Prophet, The Madman and The Broken Wings. Khalil Gibran was neglected for a long period of time by the scholars and critics but he continued working to bring improvement.</p>
                    <p><strong>Reviews:</strong> The poems in The Broken Wing are deeply personal and introspective, exploring the complexities of human relationships and the mysteries of the universe.</p>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                </div>
            </div>
        </div>
    </div>
    <!-- Modal for Book 11 -->
    <div class="modal fade" id="book11-modal" tabindex="-1" role="dialog" aria-labelledby="book11ModalLabel" aria-hidden="true">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="book11ModalLabel">War And Peace</h5>
                    <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                        <span aria-hidden="true">&times;</span>
                    </button>
                </div>
                <div class="modal-body">
                    <p><strong>Synopsis:</strong> War and Peace, historical novel by Leo Tolstoy, originally published as Voyna i mir in 1865–69. This panoramic study of early 19th-century Russian society, noted for its mastery of realistic detail and variety of psychological analysis, is generally regarded as a masterwork of Russian literature and one of the world’s greatest novels.</p>
                    <p><strong>Reviews:</strong> War and Peace was ground-breaking in its age, because up until then, war had always been something that was glorified; he looked at war through the psychology of the people experiencing it, and the way they expressed that experience in their lives. That was a profound breakthrough. For instance, he shows people suffering from post-traumatic stress.</p>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                </div>
            </div>
        </div>
    </div>
    <!-- Modal for Book 12 -->
    <div class="modal fade" id="book12-modal" tabindex="-1" role="dialog" aria-labelledby="book12ModalLabel" aria-hidden="true">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="book12ModalLabel">The Wealth Of Nations</h5>
                    <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                        <span aria-hidden="true">&times;</span>
                    </button>
                </div>
                <div class="modal-body">
                    <p><strong>Synopsis:</strong> The Wealth of Nations, work by the Scottish economist and philosopher Adam Smith, first published in 1776, that became a foundational study in the history of economics and the first formulation of a comprehensive system of political economy.</p>
                    <p><strong>Reviews:</strong> The Wealth of Nations (1776) by Adam Smith is a classic economics book that explores the principles of capitalism and its impact on society. Here's why this book is worth reading.</p>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Bootstrap JS and dependencies -->
    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.3/dist/umd/popper.min.js"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
</body>
</html>
