# python-future-proofing-apis

The following is a python spike to test "future-proofing" python APIs so that there's no
backward breakage

## Scenario

1. Imagine:

    1. Your code is written against version `1.0.0` of the API.
    2. Version `1.0.1` of the API comes out and breaks your code.

1. First of all, this is a no-no in [Semanic Versioning](https://semver.org/).
   The version MAJOR should have been raised to `2.0.0` because there's a backward compatibility breakage.
1. **But,** this confines the author of the API to raising the Semantic Versioning MAJOR often as the
   API advances.   Imaging using the API at version `132.0.5`.
1. Is there a way to advance Python APIs in a non-backward breaking manner?

## Proposal

1. Use `*args` and `**kwargs` as a part of every API method / function signature.

## Example

1. Clone this repository. The `usecase_n_calling_x...` code will
   illustrate the use of `api_version_n_...` function signatures.

1. In the example API, version 1 takes 1 parameters and version 2 takes 2 parameters.
    1. Version 1

        ```python
        def stable_api(x):
        ```

    1. Version 2

        ```python
        def stable_api(x, y):
        ```

1. In each of the following examples, the same 2 API calls are made, but each with different `import` statements.
1. In the repository directory, run:

    ```console
     python usecase_1_calling_v1.py
    ```

   Notice: Version 1 format works; version 2 does not.
1. In the repository directory, run:

    ```console
     python usecase_2_calling_v2.py
    ```

   Notice: Version 2 format works; version 1 does not.
1. In the repository directory, run:

    ```console
     python usecase_3_calling_v1_futureproofed.py
    ```

   Notice: Both version work. However, the new parameter value is ignored.
1. In the repository directory, run:

    ```console
     python usecase_4_calling_v2_futureproofed.py
    ```

   Notice: Both version work. However, the new parameter has to be "managed".
