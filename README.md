# Ex.08 Design of Interactive Image Gallery
# Date:
# AIM:
To design a web application for an inteactive image gallery with minimum five images.

# DESIGN STEPS:
## Step 1:
Clone the github repository and create Django admin interface.

## Step 2:
Change settings.py file to allow request from all hosts.

## Step 3:
Use CSS for positioning and styling.

## Step 4:
Write JavaScript program for implementing interactivity.

## Step 5:
Validate the HTML and CSS code.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
```

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Photo Gallery</title>
    <style>
        /* Basic styling */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
            text-align: center; /* Center the content */
        }
        h1 {
            font-size: 2.5em; /* Bigger font size */
            color: #fff;
            background: linear-gradient(135deg, #c8f309f7, #e6f103);
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.5);
            margin-top: 20px;
            font-weight: bold;
            letter-spacing: 1px;
        }
        h1 span {
            display: block;
            font-size: 1.5em; /* Smaller font size for the second line */
            margin-top: 5px;
        }
        .gallery {
            display: flex;
            flex-direction: row;
            justify-content: center; /* Center the gallery */
            align-items: center;
            gap: 15px;
            overflow-x: auto;
            padding: 20px;
            white-space: nowrap;
        }
        .gallery-item {
            display: inline-block;
            cursor: pointer;
        }
        .gallery-item img {
            height: 200px; /* Consistent height */
            border-radius: 10px;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .gallery-item img:hover {
            transform: scale(1.05);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }
        .modal {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 80%;
            max-width: 800px;
            background: white;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            border-radius: 10px;
            padding: 20px;
            z-index: 1000;
        }
        .modal img {
            width: 100%;
            border-radius: 10px;
        }
        .modal h2 {
            margin-top: 15px;
            text-align: center;
        }
        .modal p {
            margin-top: 10px;
            text-align: center;
        }
        .close-modal {
            display: block;
            margin: 20px auto 0;
            padding: 10px 20px;
            background: #333;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .close-modal:hover {
            background: #555;
        }
        .overlay {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            z-index: 999;
        }
    </style>
</head>
<body>
    <h1>
        M.K.SURIYA PRAKASH<br>
        <span>24901016</span><br>
        Interactive Image Gallery
    </h1>
    <div class="gallery">
        <!-- Gallery Items -->
        <div class="gallery-item" data-title="Walter white" data-description="Walter Hartwell White Sr. or Walt, also known by his pseudonym Heisenberg and frequently referred to as Mr. White, was an American chemist, school teacher, and major narcotics distributor from Albuquerque, New Mexico, whose drug empire became the largest meth operation in U.S. history, surpassing those of both Gustavo Fring and the Cartel. Before entering the drug trade, Walt worked as an overqualified high school chemistry teacher at J. P. Wynne High School while holding a second job at the A1A Car Wash to financially support his family (his wife Skyler, son Walt Jr., and infant daughter Holly). After being diagnosed with terminal lung cancer, Walt began manufacturing chemically pure methamphetamine to provide for his family upon his death. Knowing nothing about the drug trade, Walt enlisted the help of his former student, Jesse Pinkman, to sell the meth he produced." data-image="C:\Users\Suriya\Desktop\workspace\imagemapping\app\static\walter white.jpg">
            <img src="C:\Users\Suriya\Desktop\workspace\imagemapping\app\static\walter white.jpg" alt="One Piece">
        </div>
        <div class="gallery-item" data-title="Jesse pinkman" data-description="Jesse Bruce Pinkman, also known by his clandestine pseudonym and business moniker Cap'n Cook, is a former chemist, manufacturer, and distributor who worked in Albuquerque, New Mexico, currently residing in Haines, Alaska. Originally a low-level methamphetamine dealer who worked with his friend and fellow meth cook Emilio Koyama, Jesse is best known as the former business and meth cook partner of his former chemistry teacher Walter White, teaming up with Walt for two years to help him manufacture chemically pure crystal methamphetamine so Walt could provide for his family (his wife Skyler, son Walt Jr., and infant daughter Holly) upon his death. Alongside catalyzing Walt's drug empire and being the second biggest player in it after Walt himself, Jesse and Walt were also the leaders of a short-lived meth distribution chain which his friends and fellow meth distributors were also a part of." data-image="C:\Users\Suriya\Desktop\workspace\imagemapping\app\static\jesse pinkman.jpg">
            <img src="C:\Users\Suriya\Desktop\workspace\imagemapping\app\static\jesse pinkman.jpg" alt="Naruto">
        </div>
        <div class="gallery-item" data-title="Gus Fring" data-description="Gustavo Gus Fring, mockingly referred to as The Chicken Man by Hector, is a Chilean-American restaurant entrepreneur and major narcotics distributor who primarily worked in Albuquerque, New Mexico. Originally collaborating with the Mexican drug cartel to distribute their cocaine, Gus eliminated his dependence on the cartel and began distributing methamphetamine himself. Soon enough he became the kingpin of his solo drug empire, which was the most successful drug operation in United States history until his former employee Walter White surpassed it with his own drug empire." data-image="C:\Users\Suriya\Pictures\gus.jpg">
            <img src="C:\Users\Suriya\Pictures\gus.jpg" alt="Solo Leveling">
        </div>
        <div class="gallery-item" data-title="Saul Goodman" data-description="James Morgan Jimmy McGill, better known by his professional alias and business moniker Saul Goodman and later Gene Takavic, is an American criminal defense lawyer, scam artist, and convicted criminal who is serving an 86-year sentence at ADX Montrose. Originally from Cicero, Illinois during his career as a scam artist, Jimmy moved to Albuquerque, New Mexico where he worked as a lawyer, and later resided as a fugitive in Omaha, Nebraska before being caught and apprehended in a federal prison at Montrose, Colorado. During his law career, Jimmy embraced his tendencies as a former scam artist and, after becoming a dedicated and effective criminal lawyer, he began to represent criminals while he himself became increasingly involved in the city's criminal underworld, all the while slowly losing his morality along the way. Despite his flamboyant appearance and mannerisms, Saul was a highly competent lawyer who was able to solve problems and find loopholes in order to protect his clients. His business name, "Saul Goodman, is a play on the phrase "it's all good, man.""  data-image="C:\Users\Suriya\Pictures\saul godman.jpg">
            <img src="C:\Users\Suriya\Pictures\saul godman.jpg" alt="Jujutsu Kaisen">
        </div>
        <div class="gallery-item" data-title="Hank Schrader" data-description="Henry R. Hank Schrader is a high-ranking officer at the Albuquerque office of the Drug Enforcement Administration (DEA), starting out as a DEA agent alongside his close friend and partner Steven Gomez, and later being promoted to Assistant Special Agent in Charge of the DEA (ASAC). Hank is the husband of Marie Schrader and the brother-in-law of Skyler and Walter White, as well as the uncle of Walter White Jr. and Holly, having a close friendship with his nephew. As a DEA agent, Hank lead the investigations of the methamphetamine cook Heisenberg (unaware for over a year that he was actually his own brother-in-law), as well as Gustavo Fring and his drug empire. Hank is faced with numerous threats from the rival drug cartels which take a toll on his mental health, causing him to develop post traumatic stress disorder (PTSD). As a hobby, Hank home brews his own Schraderbräu beer, and also takes up mineral collecting. Despite his brashness, Hank is highly competent at his job and cares deeply about his family." data-image="C:\Users\Suriya\Pictures\Hank Schrader.jpg">
            <img src="C:\Users\Suriya\Pictures\Hank Schrader.jpg" alt="Bleach">
        </div>
       
    </div>

    <!-- Modal and Overlay -->
    <div class="overlay"></div>
    <div class="modal">
        <h2 id="modal-title"></h2>
        <img id="modal-image" src="" alt="Modal Image">
        <p id="modal-description"></p>
        <button class="close-modal">Close</button>
    </div>

    <script>
        // JavaScript for Modal and Interactivity
        document.addEventListener('DOMContentLoaded', () => {
            const galleryItems = document.querySelectorAll('.gallery-item');
            const modal = document.querySelector('.modal');
            const overlay = document.querySelector('.overlay');
            const modalTitle = document.getElementById('modal-title');
            const modalImage = document.getElementById('modal-image');
            const modalDescription = document.getElementById('modal-description');
            const closeModalButton = document.querySelector('.close-modal');

            galleryItems.forEach(item => {
                item.addEventListener('click', () => {
                    const title = item.getAttribute('data-title');
                    const description = item.getAttribute('data-description');
                    const image = item.getAttribute('data-image');

                    modalTitle.textContent = title;
                    modalDescription.textContent = description;
                    modalImage.src = image;

                    modal.style.display = 'block';
                    overlay.style.display = 'block';
                });
            });

            closeModalButton.addEventListener('click', () => {
                modal.style.display = 'none';
                overlay.style.display = 'none';
            });

            overlay.addEventListener('click', () => {
                modal.style.display = 'none';
                overlay.style.display = 'none';
            });
        });
    </script>
</body>
</html>

```
# OUTPUT:
![Screenshot 2024-12-21 114420](https://github.com/user-attachments/assets/15318725-c6f2-4e0d-b609-60dd4b6e09c5)

![Screenshot 2024-12-21 114437](https://github.com/user-attachments/assets/f65dbd94-3dcb-47dc-b15f-de7d718ed3db)

# RESULT:
The program for designing an interactive image gallery using HTML, CSS and JavaScript is executed successfully.
