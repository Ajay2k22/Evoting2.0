<script>
import { ethers } from "ethers";
import { ABI } from './Abi.js';
export default {
  name: 'Home',
  data() {
    return {
      contract: '',
      account3:'',
      contract1: '',
      provider: '',
      greet: '',
      value: '',
      signer: '',
      contractAddress: '',
      account:[],
      startelection: '',
      addcandidate: '',
      vote: '',
      authorizevoter: '',
      candidateinfo: '',
      candidate: '',
      electionname: '',
      totalvotes: '',
      owner: '',
      gettotalvotes: '',
      voters: '',
      getnumcandidates: '',



    }
  },
  methods: {
    async submitme() {
      console.log(`${this.name} ${this.email}`)
    },
    async loadproviders() {
      let contractAddress = "0xB0fC1428EAF94cb22414550372d5B34386F59665";
      let url = "http://localhost:8545";
      let provider = new ethers.providers.JsonRpcProvider("http://localhost:8545");
      // const signer = provider.getSigner()
      let signer = provider.getSigner()
      let contract = new ethers.Contract(
        contractAddress,
        ABI,
        provider
      );
      let contract1 = new ethers.Contract(
        contractAddress,
        ABI,
        signer
      );
      this.contract = contract
      this.contract1 = contract1
      this.signer = signer
      this.provider = provider
      this.contractAddress = contractAddress;


      console.log(`contract Address ${this.contract}`)
      console.log(`contract signer ${this.signer}`)



    },
    // async getGreeting() {
    //   try {
    //     let greet = await this.contract.getNumCandidates();
    //     console.log(greet)
    //     // this.greet = greet
    //     console.log('me completed')
    //   }
    //   catch (e) {
    //     console.log('error hoon')
    //     console.log(e)
    //   }
    // },

    async loader() {
      try {
        let contractAddress = "0xb9aE3528661BceD23aBC7CEF7F46FE354B47Eca0";
        let url = "http://localhost:8545";
        let provider = new ethers.providers.JsonRpcProvider(url);
        let account=await provider.listAccounts()
        this.account=account
        // const signer = provider.getSigner()
        
        console.log('signer')
        // console.log(signer3)
        let signer = provider.getSigner()
        let contract = new ethers.Contract(
          contractAddress,
          ABI,
          provider
        );
        let contract1 = new ethers.Contract(
          contractAddress,
          ABI,
          signer
        );
        this.contract = contract
        this.contract1 = contract1
        this.signer = signer
        this.provider = provider
        this.contractAddress = contractAddress;
        console.log(`contract Address ${this.contract}`)
        console.log(`contract signer ${this.signer}`)
     
        let get = await contract.electionName()
        console.log(get)
      } catch (e) {
        console.log(e)
      }
    },

    async setGreeting1() {
      try {

        let set = await this.contract1.setGreeting(this.value)
        console.log(set)

      }
      catch (e) {
        console.log(e.message)
      }
    },

    async startElection1() {
      try {
        let response = await this.contract1.startElection(this.startelection)
        console.log(`success ${response.toString()}`)
      } catch (e) {
        console.log(e)
      }
    },

    // async addCandidate1(){
    //   try{
    //     let response = await this.contract1.addCandidate(this.addcandidate)
    //     console.log(`success ${response}`)
    //   }catch(e){
    //     console.log(e)
    //   }
    // },

    async authorizeVoter1() {
      try {
        console.log(this.authorizevoter)
        let response = await this.contract1.authorizeVoter(this.authorizevoter)
        console.log(`success ${response}`)
      } catch (e) {
        console.log(e)
      }
    },

    async Vote1() {
      try {
        // let provider = new ethers.providers.JsonRpcProvider(url);
        // let account=await provider.listAccounts()
        // this.account=account
        // const signer = provider.getSigner()
        // let signer1 = this.provider.getSigner(this.account[2])
        let signer3=new ethers.providers.JsonRpcProvider("http://localhost:8545").getSigner( this.account[4] )
        let contract2 = new ethers.Contract(
          this.contractAddress,
          ABI,
          signer3
        );
        
        

        console.log(this.vote)
        let response = await contract2.vote(this.vote)
        console.log(`success from vote ${response}`)
      } catch (e) {
        console.log(e)
      }
    },

    // async candidateInfo1(){
    //   try{
    //     let response = await this.contract1.candidateInfo(this.candidateinfo)
    //     console.log(`success ${response}`)
    //   }catch(e){
    //     console.log(e)
    //   }
    // },

    // async candidate1(){
    //   try{
    //     let response = await this.contract1.candidates(this.candidate)
    //     console.log(`success ${response}`)
    //   }catch(e){
    //     console.log(e)
    //   }
    // },


    async electionName1() {
      try {
        let response = await this.contract.electionName()
        console.log(`success ${response.toString()}`)
        this.electionname = response.toString()
        console.log(`${this.electionname}`)
      } catch (e) {
        console.log(e)
      }
    },

    // async getTotalVotes1(){
    //   try{
    //     let response = await this.contract.getTotalVotes()
    //     console.log(`success ${response.toString()}`)
    //     this.totalvotes=response.toString()
    //   }catch(e){
    //     console.log(e)
    //   }
    // },

    // async getNumCandidates1(){
    //   try{
    //     let response = await this.contract.getNumCandidates()
    //     console.log(`success ${response.toString()}`)
    //     this.getnumcandidates=response.toString()
    //   }catch(e){
    //     console.log(e)
    //   }
    // },

    async owner1() {
      try {
        let response = await this.contract.owner()
        console.log(`success ${response.toString()}`)
        this.owner = response.toString()
      } catch (e) {
        console.log(e)
      }
    },

    // async totalVotes1(){
    //   try{
    //     let response = await this.contract.totalVotes()
    //     console.log(`success ${response.toString()}`)
    //     this.totalvotes=response.toString()
    //   }catch(e){
    //     console.log(e)
    //   }
    // },

    async Voters1() {
      try {
        let response = await this.contract1.voters(this.voters)
        console.log(response)
        console.log(response.authorised.toString())
        console.log(response.name.toString())
        console.log(response.whom.toString())
        console.log(response.voted.toString())

      } catch (e) {
        console.log(e)
      }
    },









  },
  mounted() {
    this.loader()

  }
}
</script>

<template>

  <div class="container">

    <div class="box">
      <label> START ELECTION </label>
      <input type="text" v-model="this.startelection" />
      <button @click="this.startElection1">click</button>
    </div>

    <div class="box">
      <label> OWNER {{ this.owner }}</label>
      <button @click="this.owner1">click</button>
    </div>

    <div class="box">
      <label> GET ELECTION NAME {{ this.electionname }} </label>
      <button @click="this.electionName1">click</button>
    </div>

    <div class="box">
      <label> AUTHORIZE VOTE </label>
      <input type="text" v-model="this.authorizevoter" />
      <button @click="this.authorizeVoter1">click</button>
    </div>

    <div class="box">
      <label> VOTERS </label>
      <input type="text" v-model="this.voters" />
      <button @click="this.Voters1">click</button>
    </div>

    <div class="box">
      <label> VOTE </label>
      <input type="text" v-model="this.vote" />
      <button @click="this.Vote1">click</button>
    </div>
    <!-- <div class="box">
      <label> ADD CANDIDATE </label>
      <input type="text" v-model="this.addcandidate" />
      <button @click="this.addCandidate1">click</button>
    </div>

    

    

    <div class="box">
      <label> CANDIDATE INFO </label>
      <input type="text" v-model="this.candidateinfo" />
      <button @click="this.candidateInfo1">click</button>
    </div>

    <div class="box">
      <label> CANDIDATE </label>
      <input type="text" v-model="this.candidate" />
      <button @click="this.candidate1">click</button>
    </div>

    

    <div class="box">
      <label> GET TOTAL VOTE {{ this.totalvotes }}</label>
      <button @click="this.getTotalVotes1">click</button>
    </div>

    

    <div class="box">
      <label> TOTAL VOTES {{ this.totalvotes }}</label>
      <button @click="Demo">click</button>
    </div>

    

    <div class="box">
      <label> NUMBER OF CANDIDATES {{ this.getnumcandidates }} </label>
      <button @click="this.getNumCandidates1">click</button>
    </div> -->
  </div>
</template>
<style scoped>
.container {
  margin: 10rem auto;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 1rem;
}

.box {
  display: flex;
  gap: 1rem;
  justify-content: center;
  align-items: center;
}
</style>