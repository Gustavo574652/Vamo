-- Script de Giros da Sorte inspirado no Blue Lock
-- Este script dá ao jogador 161 giros da sorte.
-- Certifique-se de ajustar o script para o seu jogo.

-- Número de giros da sorte a serem dados
local girosDaSorte = 161

-- Função que dá giros da sorte ao jogador
local function darGirosDaSorte(jogador)
    if jogador and jogador:FindFirstChild("leaderstats") then
        local giros = jogador.leaderstats:FindFirstChild("Giros")
        if giros then
            giros.Value = giros.Value + girosDaSorte
            print(jogador.Name .. " recebeu " .. girosDaSorte .. " giros da sorte!")
        else
            warn("Estatística 'Giros' não encontrada para o jogador " .. jogador.Name)
        end
    else
        warn("Jogador inválido ou 'leaderstats' ausente.")
    end
end

-- Evento para quando um jogador entra no jogo
game.Players.PlayerAdded:Connect(function(jogador)
    jogador.CharacterAdded:Connect(function()
        -- Dá os giros da sorte ao jogador após ele entrar no jogo
        darGirosDaSorte(jogador)
    end)
end)

-- Exemplo de comando para testar o script no console do servidor
game.Players.PlayerAdded:Connect(function(jogador)
    local leaderstats = Instance.new("Folder", jogador)
    leaderstats.Name = "leaderstats"

    local giros = Instance.new("IntValue", leaderstats)
    giros.Name = "Giros"
    giros.Value = 0 -- Inicia com 0 giros

    -- Dá os giros ao jogador
    darGirosDaSorte(jogador)
end)

-- Fim do script
