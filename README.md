<p>
    <h1 align="center">Whatsapp SDK</h1>
    <p align="center">
       Whatsapp SDK allow you to communicate with whatsapp services, just install and use. There are two types of SDKs one is
        core `whatsapp-sdk` and other one is core sdk with state management which is useful for React like application `whatsapp-sm-sdk`
    </p>
    <p align="center">
        <strong>
            <a href="https://ws-docs.bitrespond.com">Get Started!</a>
        </strong>
    </p>
    <br><br><br>
</p>

## Installation

```shell
npm install whatsapp-sdk
```

or for ReactJS

```shell
npm install whatsapp-sm-sdk
```

## Example Usage

```python
class User(Model):
    name = TextField()


u = User()
u.name = "Azeem Haider"
u.save()

# Get user
user = User.collection.get(u.key)
print(user.name)
```
