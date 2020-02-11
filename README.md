# SwiftLint CheckAllRules script

Check swift files with all [SwiftLint](https://github.com/realm/SwiftLint) rules

## Prerequisites

- Installed [SwiftLint](https://github.com/realm/SwiftLint)
- You need to remove or rename all existing `swiftlint.yml` files in directories, which you want to check.

## Usage

`./checkAllRules <pathToDir1> <pathToDir2> ...`

This command will generate swiftlint configuration file template like this:

```yml
whitelist_rules:
  - rule

included:
  - pathToDir1
  - pathToDir2
  - ...
```

Then it will substitute every SwiftLint rule one by one and collect warnings and errors data.

### Output example

```bash
Linting      185 rules

Linting rule: anyobject_protocol... OK
...
Linting rule: vertical_whitespace_between_cases... Found warnings: 5 errors: 0.
Linting rule: yoda_condition... OK

Done linting      185 rules

Suggested configuration for .swiftlint.yml :

  # Passed rules:
  # block_based_kvo
  # ...
  # xctfail_message

disabled_rules: # rule identifiers to exclude from running
  - line_length # Warnings: 19 Errors: 0
  - private_over_fileprivate # Warnings: 1 Errors: 0
  - trailing_whitespace # Warnings: 52 Errors: 0

opt_in_rules: # some rules are only opt-in
  - anyobject_protocol
  ...
  - yoda_condition
  # Failed opt-ins rules:
  # ...
  # - vertical_whitespace_between_cases # Warnings: 5 Errors: 0
```

## Author

- **Ilya Dudarenko**

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
