<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Solana Wallet Connect</title>
    <!-- Загрузите необходимые скрипты и стили для вашего Solana wallet adapter -->
</head>
<body>
    <h1>Подключите ваш Solana кошелек</h1>
    <button id="connectWallet">Подключить кошелек</button>

    <script type="module">
        // Импортируйте необходимые модули для работы с кошельком Solana
        import { Connection, PublicKey } from '@solana/web3.js';
        import { WalletAdapterNetwork } from '@solana/wallet-adapter-base';
        import { PhantomWalletAdapter } from '@solana/wallet-adapter-wallets';

        // Настройка подключения к сети Solana
        const network = WalletAdapterNetwork.Devnet;
        const endpoint = 'https://api.devnet.solana.com';
        const connection = new Connection(endpoint);

        // Создание адаптера кошелька
        const wallet = new PhantomWalletAdapter();

        // Добавление обработчика событий для кнопки подключения кошелька
        document.getElementById('connectWallet').addEventListener('click', async () => {
            try {
                // Подключение кошелька
                await wallet.connect();
                const publicKey = wallet.publicKey;
                console.log('Кошелек подключен:', publicKey.toString());
            } catch (error) {
                console.error('Ошибка подключения кошелька:', error);
            }
        });
    </script>
</body>
</html>
