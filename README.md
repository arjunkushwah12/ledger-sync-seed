# Ledger Sync Submission

## What I completed
- Fixed amount extraction bug (Rs.5 vs Rs.92,213)
- Parsed 323 transactions from 522 messages
- Generated ledger.json, summary.json, reconciliation.json
- Task 0 & 1 feedback/teardown documents

## Known issues
- Numbers don't reconcile (323 txns vs 257 expected)
- Deduplication not working (SMS + email = 2 rows, should be 1)
- MICRO category not implemented
- Email parser is stub
- Database accumulation issue on re-runs
- Task 4 (document store) not started

## How to run
./gradlew clean build
./gradlew run --args="ingest fixtures/corpus-a.jsonl"
./gradlew run --args="report submission/"

## What I'd do with more time
1. Fix dedup properly (group by acct+time+amount+merchant)
2. Implement MICRO logic (≤₹100)
3. Debug database persistence issue
4. Implement email parser
5. Build DynamoDB store

## AI disclosure
Used Claude for dedup logic. The implementation broke the pipeline, so I reverted to original.