Torrent Metadata Viewer with Authentication
This project is a graphical user interface (GUI) application built with PyQt6 and libtorrent. It provides a simple way for users to view torrent metadata, start torrent downloads, and manage user authentication. The application also features a login and registration system that stores user credentials in a JSON file.

Features
Authentication:
Users can log in or register by entering their username and password.
Registered users' credentials are stored in a users.json file.
Passwords are stored securely in plain text (for simplicity in this example; consider encrypting passwords in production).
Torrent Metadata Viewer:
Users can load a .torrent file and view its metadata, including the file name, size, and the list of files included in the torrent.
The application supports starting and monitoring torrent downloads using the libtorrent library.
It shows download progress, speed, and estimated time of arrival (ETA).
Torrent Download:
The application downloads the selected torrent file and displays the progress in a progress bar.
The download speed and ETA are updated every second.
The application will notify the user when the download is complete.
Theming and UI Enhancements:
The app is styled with custom colors for a pleasant and readable UI.
It uses animations for smooth transitions between the authentication screen and main torrent client interface.
Dependencies
To run this application, you need the following Python packages:

libtorrent (for torrent functionality)
PyQt6 (for the GUI)
json (for handling user data)
time (for ETA calculations)
Install dependencies
You can install the required dependencies using pip:

bash
Copy code
pip install libtorrent PyQt6
File Structure
bash
Copy code
/torrent_metadata_viewer/
│
├── main.py                    # Main application file
├── users.json                 # Stores registered users (username, password)
└── README.md                  # Project README
Usage
Step 1: Start the Application
Run the application by executing the following command:

bash
Copy code
python main.py
Step 2: Authentication
When you first launch the app, you'll be prompted with a login or registration screen.
Login: Enter your registered username and password to log in.
Register: If you don't have an account, you can register by providing a new username and password.
Step 3: Loading Torrent
Once logged in, you'll be able to use the torrent client:

Click the Open Torrent File button to select and load a .torrent file.
The torrent metadata, such as the name, total size, and file list, will be displayed.
Step 4: Start Download
Click Start Download to begin downloading the selected torrent file. The progress, speed, and ETA will be shown in the interface.

Step 5: Monitoring Progress
While downloading:

The progress bar will update in real-time.
The download speed (in KB/s) and ETA (estimated time to complete) will be shown.
Once the download is complete, the status label will indicate "Download completed."
Step 6: Exiting
To exit the application, simply close the window.

Code Overview
AuthenticationScreen Class
This class handles the login and registration functionality. It uses QLineEdit for username and password input fields.
It reads from and writes to a users.json file to manage user accounts.
When logging in, it checks the provided credentials and proceeds if valid; otherwise, it shows an error message.
TorrentMetadataClient Class
This class handles the main torrent functionality. It uses libtorrent for managing the torrent session, downloading files, and displaying metadata.
The user can open a .torrent file, view its metadata, and start downloading the files.
The download progress is updated using a QTimer every second.
MainApplication Class
The main application manages the authentication screen and the torrent client screen using a QStackedWidget.
It transitions between the two screens using a smooth animation when the user logs in successfully.
