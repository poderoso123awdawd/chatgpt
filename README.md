local teleportService = game:GetService("TeleportService")
local players = game:GetService("Players")
local player = players.LocalPlayer

-- Função que verifica a localização de baús de dinheiro
function findMoneyChests()
    for _, v in pairs(workspace:GetChildren()) do
        if v.Name == "MoneyChest" and v:IsA("Part") then
            return v.Position
        end
    end
    return nil
end

-- Função para teleportar o jogador para o baú de dinheiro
function teleportToMoneyChest()
    local chestPosition = findMoneyChests()
    if chestPosition then
        player.Character:SetPrimaryPartCFrame(CFrame.new(chestPosition))
        print("Teleportando para o baú de dinheiro!")
    else
        print("Nenhum baú de dinheiro encontrado.")
    end
end

-- Chamando a função para teleportar
teleportToMoneyChest()
