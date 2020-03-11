# Project code: blackcaspian

Stable coin backed by Euro. Coin name: EURO TETHER

# EURO TETHER (Euro-T)
The Euro Tether  (Euro-T )is an ERC20 compliant token backed by the Euro.
Contract Separation
The Euro Tether  (Euro-T) token is not a single smart contract; instead, it is separated into three cooperating contracts.

# ERC20Proxy
This contract exposes the functions required by the ERC20 standard, and is the only contract with which a user will need to interact with. It is the permanent interface to the Gemini dollar.

# ERC20Impl
This contract encapsulates all the logic of the Euro Tether  (Euro-T)token. ERC20Proxy delegates all execution of ERC20 functions to its trusted instance ERC20Impl.

# ERC20Store
This contract owns the storage of the Euro Tether  (Euro-T)ledger. Calls to the update functions on ERC20Store are limited to its trusted instance of ERC20Impl.

# Custodianship
Each smart contract in the Euro Tether  (Euro-T)system looks to a custodian for approval of important actions. This custodian may be another smart contract or a keyset (online or offline).

# CustodianUpgradeable
This contract provides re-usable code for custodianship and provision for passing the custodian role. All of ERC20Proxy, ERC20Impl, and ERC20Store inherit from this contract. This contract itself inherits from LockRequestable, which provides a cooperatively universally unique identifier generation scheme.

# Custodian
This contract provides general-purpose custodianship designed to be backed by an offline keyset. Approval requires dual control; time lock and revocation features are also provided.

# Upgradeability
The logical separation between the exposed ERC20 interface (ERC20Proxy), contract state (ERC20Store), and token logic (ERC20Impl) allows for upgradeability.

# ERC20ImplUpgradeable
This contract provides re-usable code for replacing the active token logic: the active instance of ERC20Impl. It itself inherits from CustodianUpgradeable as the upgrade process is controlled by the custodian. Both ERC20Proxy and ERC20Store inherit from this contract.

# Control of the Token Supply
Management of the token supply demands the security of an offline approval mechanism yet the flexibility of an online approval mechanism.

# PrintLimiter
This contract provides custodianship of ERC20Impl to govern increases to supply of Euro Tether  (Euro-T)tokens, with an offline approval mechanism granting limited privileges to an online approval mechanism.



