![image](https://user-images.githubusercontent.com/64840882/173235248-d0e8b72f-4a4f-4d4f-9e49-d6b5719fd333.png)



# Setup
It's pretty simple, once you drop the nh-context resource into your resources folder just make sure you put

ensure nh-context

in your server.cfg. 

# Examples


```
RegisterNetEvent('nh-context:testMenu', function()
    TriggerEvent('nh-context:sendMenu', {
        {
            id = 1,
            header = "Main Title",
            txt = ""
        },
        {
            id = 2,
            header = "Sub Menu Button",
            txt = "This goes to a sub menu",
            params = {
                event = "nh-context:testMenu2",
                args = {
                    number = 1,
                    id = 2
                }
            }
        },
    })
end)

RegisterNetEvent('nh-context:testMenu2', function(data)
    local id = data.id
    local number = data.number
    TriggerEvent('nh-context:sendMenu', {
        {
            id = 1,
            header = "< Go Back",
            txt = "",
            params = {
                event = "nh-context:testMenu"
            }
        },
        {
            id = 2,
            header = "Number: "..number,
            txt = "ID: "..id
        },
    })
end)
```



