# Lottery-3
Lottery.sol
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract Lottery {
    address[] public players;

    function enter() public payable {
        require(msg.value > 0.01 ether, "Not enough ETH");
        players.push(msg.sender);
    }

    function random() public view returns (uint) {
        return uint(keccak256(abi.encodePacked(block.timestamp, players.length)));
    }
}
