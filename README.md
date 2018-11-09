# ThreePhaseCommit-Socket-Programming-Java

Description:
  The program will consist of three components:
  • A passive server to relay commands between system
  • Three clients acting as transaction participants
  • One client acting as the transaction coordinator.
  
  Server:
    - The server facilitates relaying correspondence between your client processes. 
    - It will have a GUI text box that displays message between clients as they transit the server.
  
  Participant:
    - The participants will receive an arbitrary string from the coordinator in the INIT phase. 
    - Each client will have two GUI buttons that allow the user to vote to either ABORT or PREPARE-COMMIT that transaction.
    - If the user votes to ABORT, the participant will immediately relay that command to the coordinator, and the coordinator
      will initiate a GLOBAL ABORT accordingly. 
    - If the user votes to PREPARE-COMMIT, the participant will enter the PRECOMMIT state and notify the coordinator. 
    - When the coordinator responds with an ACK, the user will again be prompted to acknowledge with a button on the GUI. 
      There is no option to ABORT in this phase, just acknowledging the ACK.
    - Participants will set timers according to the 3PC protocol. 
    - If the coordinator times out, participants will check with one another on how to proceed according to 3PC.
    - If the participants receive the GLOBAL COMMIT command from the coordinator, they will save the arbitrary string 
      to non-volatile storage. 
    - Anything saved into permanent storage should be loaded into the process and displayed to the user upon 
      the process starting. 
  
  Coordinator:
    - The coordinator will accept an arbitrary string from a simple GUI that is then passed to the three participants. 
    - The participants will then be given a finite amount of time to vote on whether to PRECOMMIT or ABORT 
      writing that string to a file. 
    - If all participants respond with PRECOMMIT, the coordinator will respond with an ACK, and then issue a 
      GLOBAL COMMIT command after participants respond to the ACK.
    - The coordinator will handle votes according to 3PC. The coordinator will also implement timeouts according to 3PC.
  
  Steps of Execution:
   1.	Run the server code. Server UI will be displayed with pre-fetched information of previous session and 
   server starts running.
   2.	Run the Coordinator code
   3.	Run the Participant code.
   4.	When prompted, enter the IP Address: 127.0.0.1(localhost)
   5.	Enter the preferred screen name.( Screen name should be unique )
   6.	Apply the same procedure for running multiple participants.
   7.	The coordinator and participants are now connected and are in INIT states and the participant 
      displays previous committed messages.
   8.	Timer has stated at the participant. Let the timer run out. The participant enters ABORT.
   9.	Now send message from the coordinator. The coordinator is in WAIT state Timer has started. 
      Let the timer run out at the coordinator. The coordinator enters into ABORT.
   10. The participant is in ready state and if timer runs out contact other paticipants.
   11. The participant decide to vote either PRE COMMIT or ABORT. 
   12. Based on the votes the coordinator sends ACK or ABORT to the participants and enters into the respective state.
   13. The participant sends ACKNOWLEDGEMENT. Upon receiving the acknowledgements from all the participants, 
        the coordinator initiates Global Commit.
   14. The participant receives Global Commit, enters into COMMIT STATE and it writes the message to the file.
   15. Now again send the message from coordinator. One of the participants Votes. Now when the timer at the participant runs out. In this case ask the state of other participants. Act accordingly.
   16. The Server UI will display the messages as http format.
   17. If you want to quit close the participant window all the connected clients will be notified.
   18. The participants and coordinator will also be notified when Server is offline.
   19. Implemented multithread Server and Database for the server.



