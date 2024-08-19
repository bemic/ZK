# ZK Notes

Key properties of Zero Knowledge

* Soudness - No one can prove it without the correct secret     
    _(Usual bugs: **under-contrained** not enough conditions in circuits)_
* Completness - If I know secret I must be able to prove it     
    _(Usual bugs: **over-contrained** conditions are too strict)_
* Zero knowledge - No info leaked
    _(Not that usual: mistake in crypto algorithm implementation)_


### General resources
- [ToB - ZK docs](https://www.zkdocs.com/)
- [Rare skills - ZK book](https://www.rareskills.io/zk-book)


### Security resource
- [ToB - Disarming Fiat-Shamir footguns](https://blog.trailofbits.com/2024/06/24/disarming-fiat-shamir-footguns)
- [Paper - Weak Fiat-Shamir Attacks on Modern Proof Systems](https://eprint.iacr.org/2023/691)
- [ToB - vulnerabilities affecting Girault, Bulletproofs, and PlonK](https://blog.trailofbits.com/2022/04/13/part-1-coordinated-disclosure-of-vulnerabilities-affecting-girault-bulletproofs-and-plonk/)
- [ZK Bug tracker](https://github.com/0xPARC/zk-bug-tracker)
- [ZKSecurity - repo with reproduced bugs](https://github.com/zksecurity/zkbugs)
- [ZKSecurity blog](https://www.zksecurity.xyz/blog/)
- [ZK audit (great video)](https://www.youtube.com/watch?v=Ypreb-PKF7o)

## Crucial parts

### Fiat-shamir

It gives the ability to interactive protocols to be NON-interactive. It means only one message is necessary from prover to verifier. The interactive system is converted to the non interactive one using FS transformation. 

From:
- Prover send initial message, the commitment
- Verifier responding with a random challenge
- Prover computing final proof based on commitment and challege
- Verifier accepts or rejects


To:

- Prover inputs inital message into hash function and use the output as a random number and compute the proof
- Verifier accepts or rejects

[ToB - ZK tennis](https://blog.trailofbits.com/2021/02/19/serving-up-zero-knowledge-proofs/)

Hash function **must** be truly random.
The function strongly **depends** on the input, if initial message contains 3 elements and hash function depends only on 2, we can have same outputs while changing 1 element of the initial message.

[Pitfalls of Fiat-Shamir Heuristics](https://eprint.iacr.org/2016/771.pdf)
