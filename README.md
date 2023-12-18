# Lesson 12: Hardhat ERC20s

Lesson 12 from the Web3, Full Stack Solidity, Smart Contract & Blockchain - Beginner to Expert ULTIMATE
Course | Javascript Edition:
https://github.com/smartcontractkit/full-blockchain-solidity-course-js#lesson-12-hardhat-erc20s

Official code at:
https://github.com/PatrickAlphaC/hardhat-erc20-fcc

## Notes

* replaced
    ```javascript
    ourToken = await ethers.getContract("OurToken", deployer)
    ```
  with
    ```javascript
    const ourTokenDeployment = await deployments.get("OurToken")
    ourToken = await ethers.getContractAt(
        ourTokenDeployment.abi,
        ourTokenDeployment.address
    )
    ```
* replaced
    ```javascript
    playerToken = await ethers.getContract("OurToken", user1)
    ```
  with
    ```javascript
    const ourTokenDeployment = await deployments.get("OurToken")
    playerToken = await ethers.getContractAt(
        ourTokenDeployment.abi,
        ourTokenDeployment.address,
        await ethers.provider.getSigner(user1)
    )
    ```
* replaced
    ```javascript
    to.be.revertedWith("ERC20: insufficient allowance")
    ```
  with
    ```javascript
    to.be.revertedWithCustomError(ourToken, "ERC20InsufficientAllowance")
    ```
* replaced
    ```javascript
    ethers.utils.parseEther("5")
    ```
  with
    ```javascript
    ethers.parseEther("5")
    ```
