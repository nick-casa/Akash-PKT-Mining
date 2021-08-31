# Guide to Mining PKT on Akash at Scale

[![Guide to Mining PKT on Akash at Scale](/docs/pkt-mining.jpg)](https://www.youtube.com/watch?v=GBXEzDu5JYE "Youtube - Guide to Mining PKT on Akash at Scale")
*Click on the image above for the video guide.*

The Akash cloud is the future of cloud computing, and I was not suprised to learn that it is now paving the way for decentralized crypto mining. This project was painless and quite fun to implement and test different mining setups. I hope this guide makes it even more simple for you.

###### How it works

According to their whitepaper, "Nodes support the network by expending bandwidth, CPU time and performing encryption to mint new PKT coins into cirulcation, called *PKT Cash*." In short, the mining creates packets - called "announcements" - which are about 1kb. These announcements get pre-commited, then have a mining algorithm performed on them. Because the two main requirements are bandwith and CPU, this type of mining is optimal for the Akash network. 




---

## Step 1 ) Setting up a PKT.cash Wallet

[This](https://pkt.cash/wallet/#setup) guide on their site illustrates the different ways to set up a pkt.cash wallet. I prefer to work on Mac, so I used the Zulu Wallet GUI, which was very easy to set up. 

![Zulu GUI](/docs/zulu.png)
*Zulu GUI*

If you are using Zulu on Mac, click the "Generate New Address" button on the bottom right to make a new wallet. Each PKT wallet starts with "pkt".

**Mac Users** - I recommend Zulu Wallet for Mac ([download](https://github.com/artrepreneur/Zulu/releases))

**Windows Users** - For Windows, you can set up a wallet on Electrum ([guide](https://docs.pkt.cash/en/latest/electrum/#windows))



***

## Step 2 ) Installing Akashyltics - Deploy

1. Head over to Akashlytics and download their deploy software [here](https://akashlytics.com/deploy).
2. After installing, it will prompt you through a series of steps for either connecting or setting up an AKT wallet.

### 2.1 ) Funding Your Wallet

1. Once your wallet is set up, you will need to transfer AKT into the wallet. At the top left of the software is your akash wallet address. Utilizing your preferred AKT broker, you can either buy or transfer AKT into this wallet address. Like the PKT wallet, AKT wallets start with "akt"
2. When the wallet address has **5 AKT**, you're ready to start deploying.

### 2.2 ) Creating A Certificate

1. If this is your first time creating an Akash deployment, you will need to create a certificate. Akashlytic's Deploy tool does a good job of walking you through this. This will be located at the top right of the software

2. Once you see a serial number under the "Certicate" in the top right, you're ready to create a deployment.


### 2.3 )  Creating A Deployment

Creating a deployment is the easiest part. Once everything is linked up, replicating miners takes less than 5 minutes. 

But first, let's get antiquated with some of the terms. The decetralized computing provided by Akash is provided in what are called "deployments". You can think of a deployment as a computer hosted somewhere in the cloud. There are three important components that run this computer: vCPU, memory, and storage. 

A vCPU is a virtual CPU. 1vCPU is approximately equal to 1 CPU. Because PKT mining relies on CPU usage, this directly correlates to the speed in which you mine PKT. The more vCPUs, the faster you will rack up PKT, but the more AKT it will cost you.

Memory and storage are also both customizable under the deployments, and you can use Ki, Mi, Gi, and Ti to represent binary kilobytes, megabytes, gigabytes, and terabytes, respectfully.  These values and their correlation to the speed in which you will mine PKT are uncertain. Through testing various mining setups we can find the sweetspot where we are paying for the least amount of memory and storage and mining the most PKT.

Now that we're familiarized with the basics, let's make some miners!

1. Click "**Deployments**" on the left sidebar. 

2. Click the blue "**Create Deployment**" button in the top right.

3. This will check that you have everything needed: A balance of 5 AKT, A valid certificate on the blockchain, and a valid local certificate.

4. If you have all of these, continue. If not, check back to a previous part of the manual to fix the error.

5. Next, you will choose a template. Select "Empty" and click "**Next**"

6. Following this, copy the deploy.yml in this repository and paste it into the empty textbox. 

7. **THIS PART IS IMPORTANT**. All of the text within (and including) the double brackets "<<>>" must be removed. There are 4 main things that need to be updated in the file :

     1. PKT Wallet Address

     2. \# of vCPUs (Recommended: 10) 

     3. Amount of memory (Recommended: 1Gi)

     4. Amount of storage (Recommended: 1Gi)


8. Optional: Then, all the way at the bottom, under "deployment" you can customize the "count" field. This is how many instances of the deployment you want. So, for instance, if you have 10vCPUs and 1Gi of Memory/Storage and set the count to 2, you will have 20vCPUs and 2Gi of Memory/Storage split into two different deployments.

9. After configuring the deploy.yml, click "**Create Deployment**"

10. Soon, bids will show up, select the cheapest bid, then click "**Accept Bid**" 

11. Congratulations, your miner is up and running! 

12. Once you deploy your miner, you should see information about the deployment. Some important things to note are your amount spent, time left, and cost per month.

13. Repeat 2.3 as for as many miners as you would like to host, and make sure to set the four values in step #7. 

      

***

## Step 3 ) Analyze Deployments

Zulu Wallet makes it easy to create new PKT wallet addresses. So - with this - I have utilized this ability to track the results of several miners at once. Every time I create a new miner deployment, I add it to a new wallet address so I can track its performance. By tracking time and logging the difference in each wallet's balance, I can get a mining cost per 1 PKT. 

Another way to track this is with the [block explorer](https://explorer.pkt.cash/). If you input your PKT address, it will show mining payouts. 

This could all be automated, but I decided to use good ol' Google Sheets to analyze. This makes it easy for me to share my results with anyone reading this. 

On the left side of the sheet is the raw data collected, and on the right are some calculations. I look at each trial's speed in PKT/h, its monthly profit, cost to mine 1 PKT, and Profit Margin / ROI on multiple miner setups. 


###### My Findings

As it turns out PKT block rewards reduce by 10% every 100 days, and there are many more conditions to observe when trying to establish if a miner is profitable. Will it be profitable if AKT goes up by x%? Will it be profitable if PKT goes down by Y%? Will it be profitable in 100 days?

Below are some of the configurations that I tested, with the best miner costing about .005$/PKT 

NOTE: Some data may be inaccurate due to randomness. Trials were run in pairs of 2 side-by-side. I would like to test all of these configurations simultaneously.

All I can say is that there are definitely ways to make profitable setups now - at the end of August 2021. AKT is sitting at around $3, and PKT is about $0.02. Since the difficulty of mining will increase, we can assume the price of PKT will increase in the future, even if by a small margin. So, my strategy is going in strong now and mining while it is profitable at the current rates. My mindset is that if its profitable now, and we know if we hold it for a small time it will go up, it's a win-win. I think AKT will also rise, which will make this less profitable in the future, which also points to allocating more resources to it now.

###### Results

Get in while it's hot! As with everything in the crypto world, if your are not in early, you are late! I hope this guide has been helpful and you are successful in your mining venture.


