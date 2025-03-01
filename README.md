# Blockchain-Projects
// SPDX-License-Identifier: MIT
   pragma solidity ^0.8.0;

   contract CoffeeFarm {
       // Struct to represent a coffee batch
       struct CoffeeBatch {
           uint256 batchId;
           string farmName;
           string origin;
           uint256 harvestDate;
           uint256 roastingDate;
           string qualityGrade;
           address currentOwner;
           bool isSold;
       }

       // Mapping to store coffee batches
       mapping(uint256 => CoffeeBatch) public coffeeBatches;

       // Counter for batch IDs
       uint256 public batchCounter;

       // Function to create a new coffee batch
       function createBatch(
           string memory _farmName,
           string memory _origin,
           uint256 _harvestDate
       ) public {
           batchCounter++;
           coffeeBatches[batchCounter] = CoffeeBatch({
               batchId: batchCounter,
               farmName: _farmName,
               origin: _origin,
               harvestDate: _harvestDate,
               roastingDate: 0,
               qualityGrade: "",
               currentOwner: msg. sender,
               isSold: false
           });
       }

       // Function to get batch details
       function getBatchDetails(uint256 _batchId) public view returns (
           uint256 batchId,
           string memory farmName,
           string memory origin,
           uint256 harvestDate,
           uint256 roastingDate,
           string memory qualityGrade,
           address currentOwner,
           bool isSold
       ) {
           CoffeeBatch memory batch = coffeeBatches[_batchId];
           return (
               batch.batchId,
               batch.farmName,
               batch.origin,
               batch.harvestDate,
               batch.roastingDate,
               batch.qualityGrade,
               batch.currentOwner,
               batch.isSold
           );
       }
   }
