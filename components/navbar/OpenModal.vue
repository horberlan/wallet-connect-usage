<script setup lang="ts">
import { createWeb3Modal, defaultConfig } from "@web3modal/ethers5/vue";
import { css } from "~/styled-system/css";

const config = useRuntimeConfig();

const projectId: Ref<string | undefined> = ref(config.public.walletProjectId);
const logWalletError = ref(false);

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
  url: "http://localhost:3000",
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
  projectId: String(projectId.value),
  enableAnalytics: true, // Optional - defaults to your Cloud configuration
  enableOnramp: true, // Optional - false as default
});

watchEffect(() => {
  if (!projectId.value) {
    projectId.value = config.public.walletProjectId as string;
    logWalletError.value = true;
  } else logWalletError.value = false;
  if (logWalletError.value) console.error("your wallet is not logged in");
});
</script>

<template>
  <button
    @click="modal.open()"
    :class="
      css({
        background: 'red',
        borderRadius: '5px',
        padding: '1rem',
        cursor: 'pointer',
      })
    "
  >
    {{ !projectId ? (logWalletError = true) : projectId }}
  </button>
</template>
