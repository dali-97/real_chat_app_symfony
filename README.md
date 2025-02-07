# Symfony Real-Time Chat App with Pusher

This is a real-time chat application built with **Symfony** and **Pusher**. The application allows users to send and receive messages in real time without refreshing the page.

## Features
- 🗨️ Real-time messaging with WebSockets (via **Pusher**)
- 🛠️ Built with **Symfony** framework
- 🗄️ Messages stored in a **database** (Doctrine ORM)
- 👤 User authentication and message ownership tracking
- 🎨 Bootstrap for UI styling

## Installation

### Prerequisites
- PHP 8.x
- Composer
- Symfony CLI
- Node.js & npm
- MySQL or PostgreSQL database
- Pusher account (for WebSockets)

### 1. Clone the repository
```sh
git clone https://github.com/your-username/your-repo.git
cd your-repo
```

### 2. Install dependencies
```sh
composer install
npm install
```

### 3. Set up environment variables
Copy `.env` file and configure your database and Pusher credentials:
```sh
cp .env .env.local
```
Edit `.env.local` and update:
```
DATABASE_URL="mysql://user:password@127.0.0.1:3306/chat_app"
PUSHER_APP_ID=your_pusher_app_id
PUSHER_KEY=your_pusher_key
PUSHER_SECRET=your_pusher_secret
PUSHER_CLUSTER=your_pusher_cluster
```

### 4. Set up the database
```sh
php bin/console doctrine:database:create
php bin/console doctrine:migrations:migrate
```

### 5. Run the Symfony server
```sh
symfony serve
```

### 6. Run Webpack for assets
```sh
npm run dev
```

## Usage
1. Register or log in as a user.
2. Open the chat interface.
3. Send messages, and they will appear in real time.

## WebSockets with Pusher
Ensure your Symfony event broadcasts messages correctly to Pusher. Example:
```php
$pusher->trigger('chat', 'message-created', [
    'id' => $message->getId(),
    'content' => $message->getContent(),
    'author' => [
        'id' => $message->getSender()->getId(),
        'name' => $message->getSender()->getEmail()
    ],
    'createdAt' => $message->getCreatedAt()->format('Y-m-d H:i:s')
]);
```

## Contributing
Feel free to fork this project and submit pull requests. 🎉

## License
This project is licensed under the MIT License.

---
💡 **Follow me on GitHub for more projects!** 🚀

