
# Nwitter-Client

![Java](https://img.shields.io/badge/Java-11%2B-ED8B00?logo=openjdk&logoColor=white)
![JavaFX](https://img.shields.io/badge/JavaFX-UI_Toolkit-blue?logo=java&logoColor=white)
![Gluon Charm](https://img.shields.io/badge/Gluon_Charm-6.0.6-orange)
![GSON](https://img.shields.io/badge/GSON-2.8.6-4285F4?logo=google&logoColor=white)
![Log4j](https://img.shields.io/badge/Log4j-2.14.1-D22128?logo=apache&logoColor=white)

## Project Description

**Nwitter-Client** is the graphical frontend for the Nwitter social ecosystem. Built using **JavaFX** and **FXML**, it provides a responsive and visually engaging user experience. It communicates with the **Nwitter-Backend-Server** via raw socket connections to handle user authentication, tweet streams, and instant messaging.

Uniquely, this client implements an "Offline Mode" architecture, allowing users to draft messages and view cached content even without an active server connection, syncing data once connectivity is restored.

## Features

  * **Modern GUI:** A clean, CSS-styled interface built with JavaFX and Gluon Charm components.
  * **Real-time Timeline:** Dynamic loading and rendering of tweets (`Feed`, `Explorer`) with support for images and likes.
  * **Instant Messaging:** comprehensive chat interface supporting Direct Messages, Groups, and interaction with Bots.
  * **Offline Capability:** Robust logic to save tweets, messages, and settings locally (`offlineMessages`, `offlineSetting`) and sync later.
  * **User Management:** Graphical forms for Registration, Login, and Profile editing.
  * **Notification Center:** Visual alerts for follows, likes, and system messages.
  * **Visual Customization:** Theming support via CSS files (`segmented.css`, `styles.css`).

## System Requirements

  * **Java Development Kit (JDK):** Version 11 or higher (Required for JavaFX compatibility).
  * **JavaFX SDK:** (If not bundled with your JDK).
  * **Nwitter Server:** A running instance of the [Nwitter-Backend-Server](https://www.google.com/search?q=https://github.com/nikelroid/nwitter_server) to connect to.
  * **Dependencies:**
      * `charm-glisten-6.0.6.jar` (UI Controls)
      * `gson-2.8.6.jar`
      * `log4j-core` / `log4j-api`
      * `commons-io-2.8.0.jar`

## Detailed File Analysis & Description

The source code is located in `main/src/java/`.

### 🚀 Launch & UI Core (`launch`, `graphics`)

  * **`Main.java`**: The JavaFX Application entry point. Loads the initial stage.
  * **`Controller.java`**: Manages the flow between different scenes (Login -\> Feed -\> Chat).
  * **`graphics.java`**: Utility class for handling common UI tasks and graphical transformations.

### 📱 Pages & Layouts (`mainPages`, `resources/layout`)

  * **`Feed.java` / `Explorer.java`**: Controllers for the main timeline views.
  * **`Messenger.java`**: Manages the chat list and conversation view.
  * **`Setting.java`**: Handles user preferences.
  * **FXML Files**: The visual structure is defined in `src/resources/layout`. For example:
      * `cards/twitte.fxml`: The template for a single tweet card.
      * `page/login_page.fxml`: The login screen layout.
      * `chat/chat_sender.fxml`: Bubble layout for sent messages.

### 🔌 Connectivity (`connection`)

  * **`sender.java`**: The core networking class. It opens a socket to the server, sends JSON requests, and waits for responses.
  * **`connectionCfg.java`**: Contains IP and Port configurations (must match the Server).

### 💾 Offline Logic (`offlineMessages`, `offlineSetting`)

  * **`messageSaver.java` / `getMessageJsonSaver.java`**: Logic to serialize chat data to local JSON files when the server is unreachable.
  * **`sendMessagesToServer.java`**: A synchronization thread that pushes locally saved data when the connection is re-established.

### 🛠 Data Controllers (`jsonContoller`, `objects`)

  * **`jsonDecoder.java`**: Parses incoming JSON strings from the server into Java Objects.
  * **`objTwitte.java`, `objMessage.java`**: POJOs (Plain Old Java Objects) representing the data models.

## Installation & Running Instructions

### 1\. Clone the Repository

```bash
git clone https://github.com/nikelroid/nwitter_client.git
cd nwitter_client
```

### 2\. Configure Dependencies

Ensure all JAR files in the `lib` folder are added to your project's build path/classpath.

  * **Note:** Since this uses `charm-glisten`, ensure your IDE supports it (Gluon plugin is often helpful but not strictly required if the jar is in the classpath).

### 3\. Server Connection Setup

Open `main/src/resources/configs/connectionConfig.properties` (or the equivalent Java config file `connectionCfg.java`) and ensure the details match your backend:

```properties
host=127.0.0.1
port=8080
```

### 4\. Running the Client

Run the `Main` class.

  * **VM Options (Crucial for Java 11+):**
    You likely need to add JavaFX modules to the run configuration:
    ```
    --module-path /path/to/javafx-sdk/lib --add-modules javafx.controls,javafx.fxml
    ```

## Usage

1.  **Start the Server:** Ensure `Nwitter-Backend-Server` is running first.
2.  **Login:** Launch the client and use the Login screen.
3.  **Navigate:** Use the bottom/side navigation bar to switch between Feed, Explorer, Chat, and Settings.
4.  **Offline Mode:** If the server disconnects, you can still view loaded tweets and draft messages. They will auto-send upon reconnection.

## Contributing

Pull requests are welcome. For major changes (especially those altering the FXML structure), please open an issue first to discuss what you would like to change.

## License

Distributed under the MIT License.

## Contact

Project Maintainer - [GitHub Profile](https://github.com/nikelroid)

## Material:

Google link for download all libralies at once:
https://drive.google.com/file/d/174JtDoFYNOXHxwAt7ir7gPjp_C-TXhjz/view?usp=sharing
