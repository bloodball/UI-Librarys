local TL = {}

local TS = game:GetService("TweenService")

TL.TweenSize(obj, size, es, ed, t)
  local ti = TweenInfo.new(t, es, ed)
  local tween = TS:Create(obj, ti, {Size = size}
  tween:Play()
end

TL.TweenPosition(obj, pos, es, ed, t)
  local ti = TweenInfo.new(t, es, ed)
  local tween = TS:Create(obj, ti, {Position = pos}
  tween:Play()
end

TL.TweenColor(obj, col, t)
  local ti = TweenInfo.new(t)
  local tween = TS:Create(obj, ti, {BackgroundColor3 = col}
  tween:Play()
end

TL.TweenTransparency(obj, tp, t)
  local ti = TweenInfo.new(t)
  local tween = TS:Create(obj, ti, {BackgroundTransparency = tp}
  tween:Play()
end

TL.TweenRotation(obj, rot, t)
  local ti = TweenInfo.new(t)
  local tween = TS:Create(obj, ti, {BackgroundColor3 = col}
  tween:Play()
end

TL.TweenSizeAndPos(obj, size, pos, es, ed, t)
	local ts = game:GetService("TweenService")
	local ti = TweenInfo.new(t, es, ed)
	local tween = ts:Create(obj, ti, {Size = size, Position = pos})
	tween:Play()
end

TL.TweenAll(obj, size, pos, tran, rot, col, es, ed, t)
	local ts = game:GetService("TweenService")
	local ti = TweenInfo.new(t, es, ed)
	local tween = ts:Create(obj, ti, {Size = size, Position = pos, BackgroundTransparency = tran, Rotation = rot, BackgroundColor3 = col})
	tween:Play()
end

TL.TweenBorderSize(obj, bs, t)
	local ts = game:GetService("TweenService")
	local ti = TweenInfo.new(t)
	local tween = ts:Create(obj, ti, {BorderSizePixel = bs})
	tween:Play()
end

TL.TweenBorderColor(obj, bc, t)
	local ts = game:GetService("TweenService")
	local ti = TweenInfo.new(t)
	local tween = ts:Create(obj, ti, {BorderColor3 = bc})
	tween:Play()
end

TL.TextAnim(obj, text, t)
	for i = 1, #text, 1 do
		obj.Text = string.sub(text, 1, i)
		wait(t)
	end
end

TL.TweenTextSize(obj, txtsize, t)
	local ts = game:GetService("TweenService")
	local ti = TweenInfo.new(t)
	local tween = ts:Create(obj, ti, {TextSize = txtsize})
	tween:Play()
end

TL.TweenTP(obj, tp, t)
	local ts = game:GetService("TweenService")
	local ti = TweenInfo.new(t)
	local tween = ts:Create(obj, ti, {TextTransparency = tp})
	tween:Play()
end

TL.TweenUICorner(obj, uic, t)
	local ts = game:GetService("TweenService")
	local ti = TweenInfo.new(t)
	local tween = ts:Create(obj, ti, {CornerRadius = UDim.new(0, uic)})
	tween:Play()
end

return TL
