<script setup lang="ts">
import { createWeb3Modal, defaultConfig } from "@web3modal/ethers5/vue";

const projectId = String(process.env.WALLET_PROJECT_ID);
console.log(projectId)
const mainnet = {
  chainId: 1,
  name: "Ethereum",
  currency: "ETH",
  explorerUrl: "https://etherscan.io",
  rpcUrl: "https://cloudflare-eth.com",
};

const metadata = {
  name: "My Website",
  description: "My Website description",
  url: "https://mywebsite.com",
  icons: ["https://avatars.mywebsite.com/"],
};

const ethersConfig = defaultConfig({
  /*Required*/
  metadata,

  /*Optional*/
  enableEIP6963: true,
  enableInjected: true,
  enableCoinbase: true,
  rpcUrl: "...",
  defaultChainId: 1,
});

const modal = createWeb3Modal({
  ethersConfig,
  chains: [mainnet],
  projectId,
  enableAnalytics: true, // Optional - defaults to your Cloud configuration
  enableOnramp: true, // Optional - false as default
});
</script>

<template>
  <w3m-button />
</template>
