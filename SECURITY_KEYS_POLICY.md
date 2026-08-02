# Corporate Key Access Policy

## Scope

This policy applies to all secrets used by this repository, including private keys, RPC credentials, API keys, and automation tokens.

## Owner

- Primary owner: Repository maintainers for `Pamela-Innovation/Blockchain-for-men-blockchain-`
- Backup owner: Organization security administrator

## Key scope and permissions

- `CUSTOM_RELAYER_PRIVATE_KEY`: Dedicated relayer account only, funded with minimal operational balance.
- `*_JSON_RPC_URL`: Read/write access only required to submit and observe transactions for configured networks.
- `COVALENT_API_KEY`: Read-only API access for token valuation and metadata.

Apply least privilege:

- Use separate credentials per environment/repository when possible.
- Do not reuse high-privilege or personal keys.
- Restrict API key scopes to minimum required endpoints/features.

## Storage requirements

- Store secrets only in approved secret stores:
  - GitHub Actions repository secrets, or
  - Approved corporate vault system.
- Never store plaintext secrets in source files, `.envrc`, workflow YAML values, issues, PR comments, or logs.

## Rotation cadence

- Standard rotation: every 90 days.
- Immediate rotation triggers:
  - Suspected credential exposure.
  - Staff/owner role change.
  - Vendor or provider security incident.

## Revocation and incident response

1. Revoke the exposed key at the provider immediately.
2. Create a replacement key with minimum scope.
3. Update the secret in the approved secret store.
4. Re-run workflows and confirm successful operation.
5. Record incident details and remediation actions in internal security tracking.

## Verification checklist

- Secret names exist in GitHub Actions secrets.
- Workflows reference `${{ secrets.* }}` only.
- Repository secret scanning is run before commit/push.
- No plaintext key-like values are present in tracked files.
