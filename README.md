# Etherscan Clone

A modern blockchain explorer built with Next.js and powered by Moralis APIs, providing comprehensive Ethereum blockchain data visualization and transaction tracking capabilities.

## Features

- **Real-time Blockchain Data**: View latest blocks, transactions, and network statistics
- **Address Explorer**: Search and analyze any Ethereum address with detailed transaction history
- **Transaction Tracking**: Comprehensive transaction details including gas fees, status, and smart contract interactions
- **Token Analytics**: ERC-20 and ERC-721 token information and transfers
- **Smart Contract Verification**: View and interact with verified smart contracts
- **Network Statistics**: Live network metrics including gas prices and hash rates
- **Responsive Design**: Fully responsive interface optimized for desktop and mobile devices

## Tech Stack

- **Frontend**: Next.js 14 with App Router
- **Styling**: Tailwind CSS
- **Backend APIs**: Moralis Web3 APIs
- **Database**: PostgreSQL (optional for caching)
- **Deployment**: Vercel/Netlify compatible

## Prerequisites

Before you begin, ensure you have the following installed:

- Node.js (version 18.0 or higher)
- npm or yarn package manager
- Git

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/etherscan-clone.git
   cd etherscan-clone
   ```

2. **Install dependencies**
   ```bash
   npm install
   # or
   yarn install
   ```

3. **Set up environment variables**
   
   Create a `.env.local` file in the root directory and add the following variables:
   ```env
   # Moralis Configuration
   MORALIS_API_KEY=your_moralis_api_key_here
   NEXT_PUBLIC_MORALIS_APP_ID=your_moralis_app_id_here
   
   # Optional: Database Configuration (for caching)
   DATABASE_URL=your_database_url_here
   
   # Optional: Additional APIs
   ETHERSCAN_API_KEY=your_etherscan_api_key_here
   INFURA_PROJECT_ID=your_infura_project_id_here
   ```

## Configuration

### Moralis Setup

1. **Create a Moralis Account**
   - Visit [moralis.io](https://moralis.io) and create an account
   - Navigate to the dashboard and create a new project

2. **Get API Credentials**
   - Copy your API Key from the Moralis dashboard
   - Copy your Application ID
   - Add these to your `.env.local` file

3. **Configure Supported Networks**
   - Update the network configuration in `lib/config.js`
   - Ensure Moralis supports your target networks

### Database Setup (Optional)

For improved performance and caching:

1. **PostgreSQL Setup**
   ```bash
   # Using Docker
   docker run --name etherscan-db -e POSTGRES_PASSWORD=password -p 5432:5432 -d postgres
   ```

2. **Run Migrations**
   ```bash
   npm run db:migrate
   ```

## Development

1. **Start the development server**
   ```bash
   npm run dev
   # or
   yarn dev
   ```

2. **Open your browser**
   
   Navigate to [http://localhost:3000](http://localhost:3000) to see the application.

3. **Development Tools**
   ```bash
   # Run tests
   npm run test
   
   # Run linting
   npm run lint
   
   # Type checking
   npm run type-check
   ```

## Build and Deployment

### Local Build

```bash
# Create production build
npm run build

# Start production server
npm start
```

### Vercel Deployment

1. **Install Vercel CLI**
   ```bash
   npm install -g vercel
   ```

2. **Deploy to Vercel**
   ```bash
   vercel --prod
   ```

3. **Configure Environment Variables**
   - Add all environment variables in the Vercel dashboard
   - Ensure `MORALIS_API_KEY` and other secrets are properly configured

### Docker Deployment

```bash
# Build Docker image
docker build -t etherscan-clone .

# Run container
docker run -p 3000:3000 --env-file .env.local etherscan-clone
```

## API Endpoints

The application provides several API endpoints for blockchain data:

- `GET /api/blocks` - Latest blocks
- `GET /api/transactions` - Recent transactions
- `GET /api/address/[address]` - Address details
- `GET /api/tx/[hash]` - Transaction details
- `GET /api/tokens` - Token information

## Configuration Options

### Network Configuration

Update `lib/networks.js` to add or modify supported networks:

```javascript
export const SUPPORTED_NETWORKS = {
  ethereum: {
    chainId: 1,
    name: 'Ethereum Mainnet',
    rpcUrl: 'https://mainnet.infura.io/v3/YOUR_KEY'
  },
  polygon: {
    chainId: 137,
    name: 'Polygon',
    rpcUrl: 'https://polygon-rpc.com'
  }
}
```

### Moralis Configuration

Customize API calls in `lib/moralis.js`:

```javascript
export const moralisConfig = {
  apiKey: process.env.MORALIS_API_KEY,
  baseURL: 'https://deep-index.moralis.io/api/v2',
  timeout: 10000
}
```

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## Troubleshooting

### Common Issues

**API Rate Limits**
- Implement caching strategies
- Consider upgrading your Moralis plan
- Add request throttling

**Slow Loading Times**
- Enable database caching
- Implement proper pagination
- Optimize API calls

**Network Connection Issues**
- Verify API keys are correctly configured
- Check network connectivity
- Ensure Moralis service status

### Performance Optimization

- Enable Next.js caching strategies
- Implement proper database indexing
- Use CDN for static assets
- Optimize image loading with Next.js Image component

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

For support and questions:

- Create an issue in this repository
- Check the [Moralis documentation](https://docs.moralis.io)
- Join the [Moralis Discord community](https://discord.gg/moralis)

## Acknowledgments

- [Moralis](https://moralis.io) for providing robust Web3 APIs
- [Next.js](https://nextjs.org) for the excellent React framework
- [Etherscan](https://etherscan.io) for inspiration and reference
- The Ethereum community for continuous innovation

---

**Note**: This is a clone for educational and development purposes. Always respect the original Etherscan's terms of service and consider the ethical implications of blockchain data access.
