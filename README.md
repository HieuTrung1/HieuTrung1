local HttpService = game:GetService("HttpService")

-- Configuration section
local config = {
    imageUrl = "", -- Default image URL
    webhookUrl = ""
}

-- Function to send message with embed
local function sendMessage()
    local Data = {
        embeds = {
            {
                title = "Check",
                color = tonumber("0x7269da"),
                fields = {
                    {
                        name = "Username",
                        value = tostring(game.Players.LocalPlayer),
                        inline = true
                    },
                    {
                        name = "HakiLevel",
                        value = tostring(workspace.UserData.User_1506322528.Data.HakiLevel.value),
                        inline = true
                    }
                },
                image = {
                    url = config.imageUrl -- Use the configured image URL
                }
            }
        }
    }

    local Headers = { ["Content-Type"] = "application/json" }
    local Encoded = HttpService:JSONEncode(Data)

    local Request = http_request or request or HttpPost or syn.request
    local Final1 = {
        Url = config.webhookUrl,
        Body = Encoded,
        Method = "POST",
        Headers = Headers
    }

    Request(Final1)
end

-- Main loop to send messages
while true do
    sendMessage()
    wait(10) -- Wait 10 seconds before sending the next message
end
