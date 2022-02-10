
- deploy to testnet without localterra
- implement admin controller
    Use cw_controllers::admin to add simple admin functionality to your contract.

    1) Set up state.rs and instantiate() correctly so your contract starts its life with an admin address.

    2) Allow ExecuteMsg::UpdateAdmin and QueryMsg::GetAdmin.

    3) Write tests for the above.

- implement an admin hook to blacklist addresses and check whether `opponent` is
  blacklisted before `GameStart` msg.

      Our admin management is already implemented, but we don't have anything special for the admin to do except update to a new admin.

    1) Add cw_controller::hooks. Allow the ExecuteMsg::AddHook and ExecuteMsg::RemoveHook actions.

    2) When your contract receives an ExecuteMsg::StartGame, iterate through the blacklist to make sure that the host address is not on the blacklist.

- Finalize response message and post-game cleanup :


    It's time to use everything you've learned so far to finish the basic Rock, Paper, Scissors functionality! For this, you'll need to implement an ExecuteMsg::Respond action which continues the game. You can choose to have the message specify a game ID, but it's better to have the message specify both players and have the game looked up by those two fields.

    Either way, your code must:

    1) Check that the opponent and info.sender are the same.

    2) Compare the original host's move and the opponent's move and return the result of the game: Win, Loss, or Tie.

    3) Delete the game from state. We can save game histories in our app via Terra Observer, and they'll still be verifiable thanks to the blockchain.

    Optional: add a Leaderboard!



