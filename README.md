# mergease-sandbox

A disposable sandbox repository used to exercise Yardmaster's merge queue
against a real GitHub repository.

Pull requests opened here are queued, validated, and merged by Yardmaster
rather than merged manually. The validation workflow in
`.github/workflows/yardmaster-validation.yml` is a contract-only stub: it
checks that Yardmaster's dispatch inputs are well-formed, it does not run a
real test suite.

Nothing in this repository is production code.
