-- Script ESP vermelho para Roblox
local function marcarHumanoide()
    for _, player in pairs(game.Players:GetPlayers()) do
        if player.Character and player.Character:FindFirstChild("Humanoid") then
            if not player.Character:FindFirstChild("RedESP") then
                local highlight = Instance.new("Highlight")
                highlight.Name = "RedESP"
                highlight.FillColor = Color3.new(1, 0, 0)      -- vermelho puro
                highlight.OutlineColor = Color3.new(1, 0, 0)   -- vermelho puro
                highlight.Parent = player.Character
                highlight.Adornee = player.Character
            end
        end
    end
end

-- Marcar os existentes
marcarHumanoide()

-- Marcar sempre que um player spawnar
game.Players.PlayerAdded:Connect(function(player)
    player.CharacterAdded:Connect(function(char)
        wait(0.1)
        if char:FindFirstChild("Humanoid") then
            if not char:FindFirstChild("RedESP") then
                local highlight = Instance.new("Highlight")
                highlight.Name = "RedESP"
                highlight.FillColor = Color3.new(1, 0, 0)
                highlight.OutlineColor = Color3.new(1, 0, 0)
                highlight.Parent = char
                highlight.Adornee = char
            end
        end
    end)
end)

-- Atualizar periodicamente (para casos de respawn)
while true do
    marcarHumanoide()
    wait(2)
end
