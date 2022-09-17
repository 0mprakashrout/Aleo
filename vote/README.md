# vote.leo

`vote.leo` is a general vote program.

Anyone can propose new proposals, proposer can issue tickets to the voters, and the voter can vote without exposing privacy (with the help of Aleo's flexible privacy mechanism).

Proposal information and statistical voting results is public, while the correlation between the voter and the vote is private(protected by zk).

## Build Guide

To compile this Leo program, run:
```bash
leo build
```

## Run Guide

Make changes to `vote/inputs/vote.in` before running each command.

### Propose

Anyone can propose new proposals publicly by calling `propose` function.

Run `propose`:

```
leo run propose
```

Output sample:

```
 {
  owner: aleo1kkk52quhnxgn2nfrcd9jqk7c9x27c23f2wvw7fyzcze56yahvcgszgttu2.private,
  gates: 0u64.private,
  id: 2805252584833208809872967597325381727971256629741137995614832105537063464740field.private,
  info: {
    title: 2077160157502449938194577302446444field.private,
    content: 1452374294790018907888397545906607852827800436field.private,
    proposer: aleo1kkk52quhnxgn2nfrcd9jqk7c9x27c23f2wvw7fyzcze56yahvcgszgttu2.private
  },
  _nonce: 1639660347839832220966145410710039205878572956621820215177036061076060242021group.public
}
```

### Create Ticket

Proposer can create new tickets for proposed proposals.

Ticket is a record with `owner` and `pid`, it can be used to vote for the specific proposal - `pid`, and can only be used(voted) by the ticket `owner`.

Run `new_ticket`:

```
aleo run new_ticket
```

Output sample:

```
{
  owner: aleo1kkk52quhnxgn2nfrcd9jqk7c9x27c23f2wvw7fyzcze56yahvcgszgttu2.private,
  gates: 0u64.private,
  pid: 2264670486490520844857553240576860973319410481267184439818180411609250173817field.private,
  _nonce: 1637267040221574073903539416642641433705357302885235345311606754421919550724group.public
}
```

### Vote

Ticket owner can use the ticket to vote `agree` / `disagree` with the specific proposal - `pid`.

As the ticket record can be used as an input privately, the voter's privacy is protected by zk.

Run `agree`:

```
leo run agree
```

Run `disagree`:

```
leo run disagree
```
