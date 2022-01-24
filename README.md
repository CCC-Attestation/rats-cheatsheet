# RATS Terms Cheat Sheet

## Architecture

```
    ************   *************    ************    *****************
    * Endorser *   * Reference *    * Verifier *    * Relying Party *
    ************   * Value     *    *  Owner   *    *  Owner        *
       |           * Provider  *    ************    *****************
       |           *************          |                 |
       |                  |               |                 |
       |Endorsements      |Reference      |Appraisal        |Appraisal
       |                  |Values         |Policy           |Policy for
       |                  |               |for              |Attestation
       .-----------.      |               |Evidence         |Results
                   |      |               |                 |
                   |      |               |                 |
                   v      v               v                 |
                 .---------------------------.              |
          .----->|          Verifier         |------.       |
          |      '---------------------------'      |       |
          |                                         |       |
          |                              Attestation|       |
          |                              Results    |       |
          | Evidence                                |       |
          |                                         |       |
          |                                         v       v
    .----------.                                .---------------.
    | Attester |                                | Relying Party |
    '----------'                                '---------------'
```

### Protocol Roles

* An <a name="attester">**Attester**</a> creates attestation [Evidence](#evidence) about itself.

* A <a name="verifier">**Verifier**</a> appraises attestation [Evidence](#evidence) from an [Attester](#attester) and produces an [Attestation Result](#ar).  Appraisal is conducted according to an [Appraisal Policy for Evidence](#apfe).  Typically, [Evidence](#evidence) is compared against any applicable [Reference Values](#ref-val).  Additionally, any [Endorsements](#endo) associated with the [Attester](#attester) are also used as input into the appraisal process.

* A <a name="rp">**Relying Party**</a> appraises [Attestation Results](#ar) associated with the [Attester](#attester)'s [Evidence](#evidence) and produces a trust decision regarding the [Attester](#attester).  Appraisal is conducted according to a local [Appraisal Policy for Attestation Results](#apfar).

### Supply Chain Roles

* An <a name="endorser">**Endorser**</a> supplies [Endorsements](#endo) to the [Verifier](#verifier).

* A <a name="rv-pro">**Reference Value Provider**</a> supplies [Reference Values](#ref-val) to the [Verifier](#verifier).

### "Owners"

* A <a name="verif-owner">**Verifier Owner**</a> TODO(tho)

* A <a name="rp-owner">**Relying Party Owner**</a> TODO(tho)

## Protocol Messages

* <a name="evidence">**Evidence**</a> is TODO(tho)

* <a name="ar">**Attestation Results**</a> are TODO(tho)

* <a name="endo">**Endorsements**</a> are Attester's features that are not explicitly found in attestation Evidence.  For example: TODO(tho).

* <a name="ref-val">**Reference Values**</a> are known values describing the Attester's TCB that are expected to be found in attestation Evidence.  For example: TODO(tho).

### Policy Constructs

* An <a name="apfar">**Attestation Policy for Attestation Results**</a> TODO(tho)

* An <a name="apfe">**Attestation Policy for Evidence**</a> TODO(tho)

## Attester Structure

An Attester consists of at least one Attesting Environment and at least one Target Environment.

```
                            ^ 
                            |
                            | Evidence
                            |
  .-------------------------|----------.
  |                         |          |
  |   .----------------.    |          |
  |   | Target         |    |          |
  |   | Environment    |    |          |
  |   |                |    |          |
  |   '----------------'    |          |
  |                   |     |          |
  |                   |     |          |
  |          Collect  |     |          |
  |           Claims  |     |          |
  |                   |     |          |
  |                   v     |          |
  |                 .-------------.    |
  |                 | Attesting   |    |
  |                 | Environment |    |
  |                 |             |    |
  |                 '-------------'    |
  |               Attester             |
  '------------------------------------'

```

Attesters can be chained:

```
 .--------------------------------------------------.
 | .-----.   .------------------------------------. |
 | | RoT |<--| TE_0                               | |
 | '-----'   | .------.   .---------------------. | |
 |           | | AE_1 |<--| TE_1                | | |
 |           | '------'   | .------.   .------. | | |
 |           |            | | AE_2 |<--| TE_2 | | | |
 |           |            | '------'   '------' | | |
 |           |            '---------------------' | |
 |           '------------------------------------' |
 '--------------------------------------------------'
```
