
** Tutorial
*** Code
- Copied to /tutorial
- number_oracle.clsp
- number_guesser.clsp
*** Execution
To run the code, ensure venv activated, and from /tutorial:


number_oracle.clsp
```
MOD_HASH=$(cdv clsp treehash number_oracle.clsp)
NUMBER=1729
cdv clsp curry -a $MOD_HASH -a $NUMBER number_oracle.clsp | tee curried_number_oracle.clvm
brun curried_number_oracle.clvm '(999)'

>> ((51 0x95ef670990971e8778c905b06555d8d8cd2bb9775802ff61cd4463e4ada15373 999) (62 1729) (73 999))
```


number_guesser.clsp
```
PUBKEY=0xcafef00d
ORACLE_PUZHASH=0x0fedbeef
cdv clsp curry -a $PUBKEY -a $ORACLE_PUZHASH number_guesser.clsp | tee curried_number_guesser.clvm
brun curried_number_guesser.clvm '(1729)'

>> ((63 0x0fedbeef 1729) (50 0xcafef00d 1729))
```